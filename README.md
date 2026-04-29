# Student Result Management System

A full-stack Node.js and MongoDB app for managing student results, profiles, and downloadable result cards. It ships with a simple web UI (served from `public/`) and a REST API for authentication and student management.

## What the project does

This project provides:
- Role-based authentication (admin/teacher/student) with JWTs
- CRUD for student records and marks
- Automatic grade/percentage calculation
- Excel (.xlsx) import for bulk student creation
- Profile management with photo uploads
- PDF result card generation

## Why the project is useful

It combines a clean, single-page web UI with a lightweight API so schools or coaching centers can:
- Quickly onboard students and teachers
- Maintain marks and result history in one place
- Share printable result cards
- Update student profile details without separate tooling

## How users can get started

### Prerequisites
- Node.js 18+ (LTS recommended)
- MongoDB (local or hosted)

### Installation
```bash
cd <project-directory>
npm install
```

### Configuration
Create a `.env` file in the project root:
```env
MONGO_URI=mongodb://localhost:27017/student-results
JWT_SECRET=CHANGE_ME_USE_A_SECURE_RANDOM_SECRET
PORT=5000
```

Create the uploads folder (used for Excel imports and profile photos):
```bash
mkdir -p uploads
```

### Run the app
```bash
node server.js
```

Open the web UI at: `http://localhost:5000`

Tip: generate a strong JWT secret with `openssl rand -base64 32` (or your preferred secret manager).

### Usage examples

Register a user:
```bash
curl -X POST http://localhost:5000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"username":"teacher1","password":"pass123","role":"teacher"}'
```

Login and use the token:
```bash
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username":"teacher1","password":"pass123"}'
```

Then include the token in API requests:
```bash
curl http://localhost:5000/api/students \
  -H "Authorization: Bearer <token>"
```

## Where users can get help

- Open an issue in this repository for bugs or feature requests
- Review the source in `routes/`, `controllers/`, and `models/` to understand API behavior

## Who maintains and contributes

Maintained by **@shubhamvrs** and community contributors.

Contributions are welcome:
- Fork the repository
- Create a feature branch
- Open a pull request with a clear description of changes
