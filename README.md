# Task Management System Backend

A backend API for a **task management, project tracking, and team collaboration** platform.  
Built with **FastAPI**, **PostgreSQL**, and **Redis**, the system supports **task assignments**, **progress tracking**, real-time updates, and **collaboration features**.  
**Celery** is used for background jobs, and **Docker** ensures easy deployment.

---

## 🚀 Features

- **User Authentication & Authorization**  
  - JWT-based authentication  
  - Role-based access control (Admin, Project Manager, Team Member)

- **Task & Project Management**  
  - CRUD operations for tasks and projects  
  - Task assignment to team members  
  - Project milestones and deadlines

- **Collaboration Tools**  
  - Comments on tasks  
  - Activity logs and audit trails

- **Productivity Enhancements**  
  - Redis caching for faster reads  
  - Background jobs (notifications, reminders) via Celery  
  - Scheduled tasks (e.g., daily progress reports)

- **Developer-Friendly**  
  - OpenAPI Docs (`/docs`)  
  - Docker-based setup  
  - Easily extendable with new microservices

---

## 🛠 Tech Stack

**Backend:** [FastAPI](https://fastapi.tiangolo.com/) (Python)  
**Database:** [PostgreSQL](https://www.postgresql.org/)  
**Caching / Queue Broker:** [Redis](https://redis.io/)  
**Background Jobs:** [Celery](https://docs.celeryproject.org/)  
**Deployment:** Docker & Docker Compose  
**Frontend (separate repo):** [Vite + React](https://vitejs.dev/)  

---

## 📂 Project Structure

backend/
├── app/
│ ├── main.py # FastAPI entry point
│ ├── api/ # API route definitions
│ ├── models/ # SQLAlchemy models
│ ├── schemas/ # Pydantic validation schemas
│ ├── tasks/ # Celery task definitions
│ ├── core/ # Config, auth, middleware
│ └── utils/ # Helper functions (caching, security)
├── celery_worker.py # Celery app initialization
├── requirements.txt
├── docker-compose.yml
└── README.md


---

## ⚙️ Setup & Installation

### 1️⃣ Prerequisites

- Python 3.10+
- Docker & Docker Compose installed
- PostgreSQL
- Redis

### 2️⃣ Clone the Repository

git clone https:/github.com/tanishqsrivastavaa/task-management-system.git

cd task-management-system


### 3️⃣ Environment Variables

Copy `.env.example` to `.env` and fill in your credentials:
DATABASE_URL=postgresql+psycopg2://user:password@db:5432/taskdb
REDIS_URL=redis://redis:6379/0
JWT_SECRET=your_jwt_secret_key
JWT_ALGORITHM=HS256


### 4️⃣ Build and Start with Docker
docker-compose up --build


### 5️⃣ Run Database Migrations
docker-compose exec backend alembic upgrade head

---

## 📜 API Documentation

Once running, API docs are available at:

- **Swagger UI:** [http://localhost:8000/docs](http://localhost:8000/docs)
- **ReDoc:** [http://localhost:8000/redoc](http://localhost:8000/redoc)

---

## 🧵 Background Jobs (Celery)

- **Start Worker:**
docker-compose exec backend celery -A app.tasks worker --loglevel=

- **Start Beat Scheduler (for periodic tasks):**
docker-compose exec backend celery -A app.tasks beat --loglevel=info


Common use cases:
- Sending deadline reminders
- Sending activity summary emails
- Generating reports in the background

---

## 🧪 Running Tests
docker-compose exec backend pytest

---

## 🤝 Contributing

Pull requests are welcome!  
Please create a feature branch and submit your changes via a PR.

---




