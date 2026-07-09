# JWT Authentication + CRUD Notes Demo

A beginner-friendly full-stack application demonstrating **JWT (JSON Web Token) Authentication** with a protected **CRUD Notes API**.

The backend is built with **Node.js + Express**, while the frontend is built using **React + Vite**.

---

# Features

## Authentication

- User Registration
- User Login
- Password hashing using bcryptjs
- JWT token generation
- Protected API routes
- Token expiration (1 hour)

---

## Notes CRUD

Authenticated users can:

- Create notes
- View only their own notes
- Update their own notes
- Delete their own notes

Each user's notes are private.

---

# Technologies Used

## Backend

- Node.js
- Express.js
- CORS
- JSON Web Token (jsonwebtoken)
- bcryptjs

## Frontend

- React
- Vite
- Fetch API
- CSS

---

# Project Structure

```
project-folder/

│
├── backend/
│     └── index.js
│
├── frontend/
│     ├── src/
│     │     ├── App.jsx
│     │     ├── App.css
│     │     └── main.jsx
│     │
│     └── package.json
│
└── README.md
```

---

# Installation

## Backend

Go to backend folder

```bash
cd backend
```

Install dependencies

```bash
npm install
```

Run server

```bash
node index.js
```

Server starts on

```
http://localhost:5000
```

---

## Frontend

Go to frontend folder

```bash
cd frontend
```

Install dependencies

```bash
npm install
```

Start React application

```bash
npm run dev
```

Usually runs on

```
http://localhost:5173
```

---

# Backend API

---

## Register User

**POST**

```
/register
```

Request

```json
{
  "username": "alice",
  "password": "1234"
}
```

Response

```json
{
  "message": "Account created! You can now log in."
}
```

---

## Login

**POST**

```
/login
```

Request

```json
{
  "username": "alice",
  "password": "1234"
}
```

Response

```json
{
  "token": "JWT_TOKEN"
}
```

---

# Authorization

For every protected route include the JWT token.

Header

```
Authorization: Bearer YOUR_TOKEN
```

---

# Create Note

**POST**

```
/notes
```

Body

```json
{
  "text": "Learn JWT"
}
```

Response

```json
{
  "id": 1,
  "username": "alice",
  "text": "Learn JWT"
}
```

---

# Get Notes

**GET**

```
/notes
```

Response

```json
[
  {
    "id": 1,
    "username": "alice",
    "text": "Learn JWT"
  }
]
```

---

# Update Note

**PUT**

```
/notes/:id
```

Body

```json
{
  "text": "Updated Note"
}
```

Response

```json
{
  "id": 1,
  "username": "alice",
  "text": "Updated Note"
}
```

---

# Delete Note

**DELETE**

```
/notes/:id
```

Response

```
204 No Content
```

---

# Authentication Flow

```
Register
      │
      ▼
Login
      │
      ▼
Receive JWT Token
      │
      ▼
Store Token
      │
      ▼
Send Token in Authorization Header
      │
      ▼
Protected API Access
```

---

# Password Security

Passwords are never stored in plain text.

Instead,

```
Password
      │
      ▼
bcrypt Hash
      │
      ▼
Stored in Server
```

During login,

```
Entered Password
       │
       ▼
bcrypt.compare()
       │
       ▼
Match?
       │
       ▼
JWT Generated
```

---

# JWT Flow

```
User Login
      │
      ▼
Server verifies password
      │
      ▼
JWT Token created
      │
      ▼
Frontend stores token
      │
      ▼
Every API request includes

Authorization:
Bearer TOKEN

      │
      ▼
Server verifies JWT
      │
      ▼
Access Granted
```

---

# Demo Workflow

1. Register a new account.
2. Login using the same credentials.
3. Receive a JWT token.
4. Add notes.
5. View your notes.
6. Edit notes.
7. Delete notes.
8. Logout.

---

# Sample Users

Example

Username

```
alice
```

Password

```
1234
```

You can also create any username because the application stores users in memory.

---

# Important Notes

- This application uses an in-memory database.
- Restarting the backend removes all users and notes.
- JWT expires after one hour.
- Notes are accessible only by their owner.

---

# Future Improvements

- MongoDB or MySQL database
- Refresh Tokens
- User Profile
- Change Password
- Email Verification
- Forgot Password
- Role-based Authorization (Admin/User)
- Persistent Login
- Docker Support
- Deployment to Render or Railway

---

# Learning Outcomes

This project demonstrates:

- Express REST API
- React Frontend
- JWT Authentication
- Password Hashing
- Middleware
- Authorization
- CRUD Operations
- Fetch API
- React Hooks
- Protected Routes
- Secure API Design

---

# License

This project is for educational purposes and learning JWT Authentication using Node.js, Express, and React.
