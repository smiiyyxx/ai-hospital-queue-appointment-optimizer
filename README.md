# 🏥 AI-Powered Hospital Queue & Appointment Optimization System

An end-to-end prototype designed to reduce patient waiting time and support hospital staff with **appointment management, priority-based queueing, waiting-time estimation, analytics, and a future GenAI operations assistant**.

> **Current status:** Working MVP. The queue engine currently uses transparent rules. The ML and GenAI layers are intentionally separated so they can be added and evaluated without hiding the core scheduling logic.

---

## 🎯 Problem Statement

Hospitals can experience long and unpredictable waiting times when appointment volume, emergency cases, doctor availability, and walk-in patients change throughout the day.

The goal of this project is to build a decision-support platform that can:

- manage appointments
- prioritize urgent cases
- organize department queues
- estimate waiting time
- show operational load
- provide an AI assistant for staff in a later phase

The system is intended to **support**, not replace, clinical decisions.

---

## ✨ Core Features

### 👤 Appointment Management
- Patient registration
- Department and doctor selection
- Appointment time
- Emergency-case flag
- Arrival-delay capture

### 🚦 Queue Optimization
- Priority-based queue ordering
- Emergency-case prioritization
- Queue-position calculation
- Transparent waiting-time estimate

### 📊 Operational Analytics
- Total appointments
- Department workload
- Queue size
- Estimated waiting time

### 🤖 Planned AI Layer
The next version can add:
- ML-based waiting-time prediction
- department congestion prediction
- GenAI operations assistant
- RAG over hospital policies and operational documents

---

## 🧠 System Workflow

```text
Patient / Receptionist
        ↓
Appointment Registration
        ↓
MySQL Database
        ↓
Priority & Queue Engine
        ↓
Queue Position
        ↓
Estimated Waiting Time
        ↓
Operational Dashboard
        ↓
ML Prediction + GenAI Assistant
```

---

## 🏗️ Architecture

```text
┌───────────────────────────────┐
│        Web Dashboard          │
│       HTML / CSS / JS         │
└───────────────┬───────────────┘
                │ HTTP / JSON
                ▼
┌───────────────────────────────┐
│        FastAPI Backend        │
│ Appointment + Queue APIs      │
└───────────────┬───────────────┘
                │
        ┌───────┴────────┐
        ▼                ▼
┌──────────────┐  ┌─────────────────┐
│    MySQL     │  │ Queue Engine    │
│ Patient data │  │ Priority logic  │
│ Appointments │  │ Wait estimate   │
└──────────────┘  └────────┬────────┘
                            │
                            ▼
                    ┌──────────────┐
                    │ AI / ML      │
                    │ Future layer │
                    └──────────────┘
```

---

## 🗂️ Project Structure

```text
ai-hospital-queue-optimizer/
│
├── app/
│   ├── main.py
│   ├── database.py
│   ├── models.py
│   ├── schemas.py
│   ├── queue_engine.py
│   ├── templates/
│   │   └── index.html
│   └── static/
│       └── styles.css
│
├── scripts/
│   ├── create_database.sql
│   └── seed_demo.py
│
├── data/
├── model/
├── docs/
│
├── .env.example
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 🛠️ Technology Stack

### Current MVP
- Python
- FastAPI
- MySQL
- SQLAlchemy
- HTML
- CSS
- JavaScript
- REST API

### Planned intelligence layer
- Pandas
- Scikit-learn
- Generative AI / LLM
- RAG
- Plotly

### Engineering / deployment
- Git
- GitHub
- Docker

Technologies under “planned” should only be moved to the resume after they are actually implemented and understood.

---

## 🚀 Run Locally

### 1. Create the MySQL database

Open MySQL and run:

```sql
CREATE DATABASE hospital_queue;
```

### 2. Create a virtual environment

Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure the database

Copy:

```text
.env.example
```

to:

```text
.env
```

Then set your MySQL connection:

```text
DATABASE_URL=mysql+pymysql://root:YOUR_PASSWORD@localhost:3306/hospital_queue
```

### 5. Start the API

```bash
uvicorn app.main:app --reload
```

Open:

```text
http://127.0.0.1:8000
```

API documentation is available at:

```text
http://127.0.0.1:8000/docs
```

---

## 🔌 API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/` | Dashboard |
| GET | `/api/health` | Health check |
| POST | `/api/appointments` | Create appointment |
| GET | `/api/queue/{department}` | View department queue |
| GET | `/api/analytics` | Operational statistics |

---

## 🧪 Example Queue Logic

The current prototype uses an intentionally simple and explainable rule:

```text
Emergency case
      ↓
Highest priority

Normal appointment
      ↓
Base priority

Late arrival / waiting time
      ↓
Small priority adjustment
```

The waiting-time baseline is:

```text
Estimated wait = patients ahead × average service time
```

This is deliberately a baseline rather than pretending that a simple formula is a production-grade prediction model.

---

## 🤖 GenAI Roadmap

The GenAI assistant will eventually allow hospital staff to ask questions such as:

> "Which department has the highest waiting load?"

> "Why is the emergency queue delayed?"

> "Summarize today's appointment pressure."

> "What operational changes could reduce waiting time?"

For trustworthy answers, the assistant should retrieve relevant structured analytics and approved hospital policy information before generating a response.

---

## 📈 ML Roadmap

A later model can learn from historical operational data using features such as:

- department
- appointment hour
- day of week
- number of patients waiting
- emergency count
- doctor availability
- average service time
- historical no-show rate

The model can estimate:

```text
Expected waiting time
```

and compare that prediction with the current rule-based estimate.

---

## 🔐 Privacy & Safety

This is an educational prototype.

A production hospital system would require:

- strong authentication and authorization
- encryption
- audit logs
- privacy controls
- validated clinical workflows
- secure handling of patient information
- human oversight
- extensive testing

Do not use real patient data in this repository.

---

## 🔮 Future Improvements

- React dashboard
- JWT authentication
- Doctor and receptionist roles
- Real-time queue updates
- ML waiting-time prediction
- No-show prediction
- GenAI operations assistant
- RAG over hospital policies
- Interactive Plotly analytics
- Docker deployment
- Cloud deployment
- Automated testing
- Monitoring and audit logging

---

## 📌 Project Goal

The project demonstrates how **backend engineering, relational databases, queue algorithms, analytics, machine learning, and Generative AI** can work together to address a practical hospital operations problem.

---

## 👩‍💻 Author

**Smruti Smaranika Panda**

Python | Java | SQL | AI / GenAI | Data Analysis
