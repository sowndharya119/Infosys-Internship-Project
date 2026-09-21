Team-B Petition Management System

A full-stack web-based Petition Management System developed as part of the Infosys Springboard Internship.

The system provides a digital platform for users to create and manage petitions, participate in polls, submit reports, track verification status, and receive notifications. It also includes a dedicated administration panel for managing the application.

📌 Table of Contents

Project Overview

Objectives

Key Features

System Architecture

Application Flow

Petition Workflow

User Roles

Project Structure

Technology Stack

Database Structure

Getting Started

Environment Variables

Running the Project

Authentication Flow

Admin Panel Flow

Security Features

Deployment

Future Enhancements

Project Information

GitHub Repository

🎯 Project Overview

The Team-B Petition Management System is designed to provide a centralized digital platform for civic engagement.

Users can:

Register and securely log in

Create petitions

View and participate in petitions

Create and participate in polls

Submit reports

Track verification status

Receive notifications

View officials and relevant information

Administrators can manage users, petitions, polls, reports, notifications, and verification-related activities through a separate admin panel.

🎯 Objectives

The major objectives of the system are:

Provide a centralized platform for digital petitions.

Allow users to create and participate in petitions.

Enable users to track petition-related activities.

Provide polling functionality for civic participation.

Support report submission and management.

Provide verification-related functionality.

Provide notifications for important activities.

Provide administrators with a dedicated management interface.

Protect sensitive user information through authentication and security mechanisms.

Provide a scalable architecture for future enhancements.

✨ Key Features

👤 User Management

User registration

Login authentication

OTP-based signup

Forgot password

Password reset

JWT-based authentication

Protected routes

Role-based access control

📝 Petition Management

Create petitions

View petitions

Filter petitions

Track petition status

Support/sign petitions

Manage petition information

📊 Poll Management

Create polls

View available polls

Participate in polls

Record votes

View poll results

📢 Notification Management

User notifications

Activity notifications

System updates

📄 Report Management

Submit reports

View report information

Admin management of reports

🔐 Verification

Upload verification documents

Track verification status

Manage verification information

👨‍💼 Admin Panel

The dedicated admin panel provides administrative functionality for:

User management

Petition management

Poll management

Report management

Verification management

Notification management

Dashboard monitoring

🏗️ System Architecture

flowchart TD

    U[User / Citizen] --> FE[React Frontend]

    FE --> AUTH[Authentication]
    FE --> PET[Petition Management]
    FE --> POLL[Poll Management]
    FE --> REPORT[Report Management]
    FE --> VERIFY[Verification]
    FE --> NOTIFY[Notifications]

    AUTH --> API[Node.js + Express API]
    PET --> API
    POLL --> API
    REPORT --> API
    VERIFY --> API
    NOTIFY --> API

    API --> MW[Authentication & Role Middleware]

    MW --> CTRL[Controllers]
    CTRL --> SERVICES[Services]
    SERVICES --> DB[(MongoDB)]

    SERVICES --> EMAIL[Email Service]

    ADMIN[Administrator] --> AP[Admin Panel]
    AP --> API

🔄 Application Flow

flowchart TD

    A[Open Application] --> B{Existing User?}

    B -->|No| C[Register]
    C --> D[OTP Verification]
    D --> E[Account Created]

    B -->|Yes| F[Login]
    E --> F

    F --> G{Valid Credentials?}

    G -->|No| H[Display Error]
    H --> F

    G -->|Yes| I[Generate JWT]

    I --> J[User Dashboard]

    J --> K[Petitions]
    J --> L[Polls]
    J --> M[Reports]
    J --> N[Verification]
    J --> O[Notifications]

    K --> P[Backend API]
    L --> P
    M --> P
    N --> P
    O --> P

    P --> Q[(MongoDB)]
    Q --> R[API Response]
    R --> J

📝 Petition Workflow

flowchart LR

    A[User Login] --> B[Create Petition]

    B --> C[Enter Petition Details]

    C --> D[Submit Petition]

    D --> E[Backend Validation]

    E --> F[(MongoDB)]

    F --> G[Petition Published]

    G --> H[Other Users View Petition]

    H --> I[Support / Sign Petition]

    I --> J[Signature Recorded]

    J --> K[Petition Progress]

    K --> L[Admin / Official Review]

    L --> M[Status Update]

    M --> N[User Notification]

👥 User Roles

Citizen / User

Users can:

Register and log in

Create petitions

View petitions

Support petitions

Participate in polls

Submit reports

Track verification status

Receive notifications

Administrator

Administrators can:

Manage users

Manage petitions

Manage polls

Manage reports

Manage verification

Manage notifications

Monitor dashboard information

Officials

The system provides functionality for displaying and managing official-related information.

📁 Project Structure

Infosys-Internship-Project/
│
├── backend/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── services/
│   ├── utils/
│   ├── package.json
│   └── server.js
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   └── App.jsx
│   ├── package.json
│   └── vite.config.js
│
├── admin-panel/
│   ├── public/
│   ├── package.json
│   └── server.js
│
├── .gitignore
├── LICENSE
└── README.md

🛠️ Technology Stack

Component

Technology

Frontend

React.js

Styling

Tailwind CSS

Backend

Node.js

API Framework

Express.js

Database

MongoDB

Authentication

JWT

Password Hashing

bcrypt

Email Service

SMTP / Gmail

Build Tool

Vite

Version Control

Git & GitHub

🗄️ Database Structure

The application uses MongoDB as its database.

User
 │
 ├── Petition
 │      └── Signature
 │
 ├── Poll
 │      └── Vote
 │
 ├── Report
 │
 ├── Notification
 │
 └── VerificationDocument

Main Collections

User – Stores user information and authentication details.

Petition – Stores petition details.

Signature – Stores petition participation/signatures.

Poll – Stores poll information.

Vote – Stores poll votes.

Report – Stores submitted reports.

Notification – Stores user notifications.

VerificationDocument – Stores verification-related information.

⚙️ Getting Started

Prerequisites

Make sure the following software is installed:

Node.js

npm

MongoDB or MongoDB Atlas

Git

Check Node.js:

node --version

Check npm:

npm --version

📥 Clone the Repository

git clone https://github.com/sowndharya119/Infosys-Internship-Project.git

Navigate to the project:

cd Infosys-Internship-Project

📌 Environment Variables

Create a .env file inside the backend/ folder:

backend/.env

Use the following template:

PORT=5000

MONGO_URI=your_mongodb_connection_string

JWT_SECRET=your_jwt_secret

FRONTEND_URL=http://localhost:5173

ENCRYPTION_KEY=your_secure_64_character_hex_key

EMAIL_FROM=your_email@example.com

MAX_FILE_SIZE=10485760
MAX_FILES_PER_REQUEST=5

BCRYPT_ROUNDS=12

JWT_EXPIRY=24h
PASSWORD_RESET_EXPIRY=3600000

LOGIN_RATE_LIMIT=5
LOGIN_RATE_WINDOW=300000

GENERAL_RATE_LIMIT=100
GENERAL_RATE_WINDOW=900000

NODE_ENV=development

EMAIL_ENABLED=true

SMTP_HOST=smtp.gmail.com
SMTP_USER=your_email@gmail.com
SMTP_PASSWORD=your_gmail_app_password
SMTP_PORT=587
SMTP_SECURE=false

APP_NAME=Civix

⚠️ Security Note

Never upload the actual .env file to GitHub.

Do not expose:

MongoDB usernames or passwords

MongoDB connection strings containing credentials

JWT secrets

Encryption keys

Gmail passwords

SMTP credentials

API keys

Keep the real values only in your local backend/.env file.

Make sure .env is included in .gitignore.

▶️ Running the Project

1. Backend

Open a terminal:

cd backend
npm install
npm run dev

The backend will run on the port specified in the .env file.

2. Frontend

Open another terminal:

cd frontend
npm install
npm run dev

The frontend will normally be available at:

http://localhost:5173

3. Admin Panel

Open another terminal:

cd admin-panel
npm install
npm run start

The admin panel is available at:

http://localhost:5050

🔑 Admin Login

For development/testing, use the administrator credentials configured in your local development environment.

Security: Actual administrator credentials should not be stored in this README or committed to GitHub.

🔐 Authentication Flow

sequenceDiagram

    participant User
    participant Frontend
    participant Backend
    participant MongoDB

    User->>Frontend: Enter Login Details

    Frontend->>Backend: Login Request

    Backend->>MongoDB: Validate User

    MongoDB-->>Backend: User Details

    Backend->>Backend: Generate JWT

    Backend-->>Frontend: JWT Token

    Frontend-->>User: Dashboard

    User->>Frontend: Access Protected Page

    Frontend->>Backend: Request + JWT

    Backend->>Backend: Verify JWT

    Backend->>MongoDB: Fetch Data

    MongoDB-->>Backend: Data

    Backend-->>Frontend: API Response

    Frontend-->>User: Display Data

📊 Admin Panel Flow

flowchart TD

    A[Administrator] --> B[Admin Login]

    B --> C{Valid Credentials?}

    C -->|No| D[Login Error]
    D --> B

    C -->|Yes| E[Admin Dashboard]

    E --> F[User Management]
    E --> G[Petition Management]
    E --> H[Poll Management]
    E --> I[Report Management]
    E --> J[Verification Management]
    E --> K[Notification Management]

    F --> L[Backend API]
    G --> L
    H --> L
    I --> L
    J --> L
    K --> L

    L --> M[(MongoDB)]

🧩 Backend Architecture

The backend follows a modular architecture:

Client Request
      │
      ▼
    Routes
      │
      ▼
  Middleware
      │
      ▼
  Controllers
      │
      ▼
   Services
      │
      ▼
    Models
      │
      ▼
   MongoDB

This structure separates routing, authentication, business logic, and database operations.

🎨 Frontend Architecture

React Application
       │
       ├── Components
       │
       ├── Pages
       │
       ├── Services
       │
       ├── Authentication
       │
       └── API Integration
                │
                ▼
          Express Backend

🛡️ Security Features

The application includes:

JWT-based authentication

Role-based authorization

Password hashing using bcrypt

Protected API routes

Admin authentication middleware

Rate limiting

File upload restrictions

Password reset expiry

JWT expiry

Environment variable configuration

Encryption utilities

Request validation

🌐 Deployment

The application can be deployed using cloud platforms.

Frontend

Possible deployment platforms:

Vercel

Netlify

Backend

Possible deployment platforms:

Render

Railway

AWS

Database

MongoDB Atlas can be used for cloud database hosting.

🚀 Future Enhancements

Potential future improvements include:

Real-time notifications

Advanced analytics dashboard

AI-based petition categorization

Multilingual support

Mobile application

Advanced search and filtering

Petition recommendation system

Improved document verification

Cloud file storage

Real-time petition updates

Automated CI/CD deployment

📚 Project Information

Item

Details

Project

Team-B Petition Management System

Internship

Infosys Springboard Internship

Domain

Digital Civic Engagement

Application Type

Full-Stack Web Application

Architecture

Client-Server Architecture

Database

MongoDB

Backend

Node.js + Express.js

Frontend

React.js

Version Control

Git + GitHub

👨‍💻 Team

Developed collaboratively by Team-B as part of the Infosys Springboard Internship.

🔗 GitHub Repository

Infosys Internship Project

📄 License

This project is developed as part of the Infosys Springboard Internship.
