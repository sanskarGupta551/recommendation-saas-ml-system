# recommendation-saas-ml-system

**End-to-end, enterprise-ready SaaS recommendation platform powered by live Reddit data. Features modular ML pipelines, robust feedback loops, interactive dashboards, admin analytics, automated CI/CD, hybrid on-premises/cloud deployment (Terraform), and fully reproducible MLOps workflows.**

## 🚀 Overview

This project delivers a full-stack, production-grade recommendation system built as a SaaS application with real Reddit data. It supports easy deployment on-premises or in the cloud (AWS, GCP, Azure) using modular Terraform scripts.

**Key Features:**
- Live Reddit data ingestion (via API)
- Advanced recommendation engine (collaborative/content/hybrid)
- Interactive user/admin dashboards
- CI/CD for code and models
- Monitoring, drift detection, retraining triggers
- Role-based authentication
- Reproducible, one-command deployment for all environments

## 📦 Project Structure

```
/
├── api/          # FastAPI (or Django) backend, ML inference, business logic
├── frontend/     # React/Streamlit/Gradio dashboards (user & admin UI)
├── etl/          # Reddit data ingestion, preprocessing, feature engineering
├── models/       # ML model training, tracking, inference code
├── infra/
│     ├── terraform/  # IaC scripts: on-prem, AWS, GCP, Azure
│     └── docker/     # Docker/Compose configs
├── docs/         # Setup, architecture, usage documentation
├── tests/        # Unit, integration, E2E tests for all major modules
├── scripts/      # Helper utilities (demo data, setup, CLI automation)
├── configs/      # YAML/JSON/env config templates for all environments
├── notebooks/    # Data analysis, prototyping, ML experiments
└── README.md     # Project overview, instructions, and links
```

## 🛠️ Quickstart

### 1. **Prerequisites**

- Python 3.9+
- Node.js (for React UI)
- Docker & Docker Compose (for local deployment)
- Terraform (for infra automation)
- Reddit API credentials ([Get them here](https://www.reddit.com/prefs/apps))
- Cloud CLI (if deploying to AWS/GCP/Azure)

### 2. **Clone the Repository**

```bash
git clone https://github.com/yourusername/recommendation-saas-ml-system.git
cd recommendation-saas-ml-system
```

### 3. **Setup Environment Variables**

Create a `.env` file in the root directory with these variables:

```
REDDIT_CLIENT_ID=your_client_id
REDDIT_CLIENT_SECRET=your_secret
REDDIT_USER_AGENT=your_agent_name
DATABASE_URL=your_db_connection_string
SECRET_KEY=your_app_secret
```

### 4. **Local (On-Prem) Deployment**

**A. Start with Docker Compose**

```bash
docker-compose up --build
```
System runs:
- FastAPI backend at `http://localhost:8000`
- Frontend dashboard at `http://localhost:3000` (if React)
- Local databases (Postgres/NoSQL)

**B. One-Command Provision/Cleanup with Terraform**

```bash
cd infra/terraform/onprem
terraform init
terraform apply         # To provision VMs, DB, K8s/Swarm infra
terraform destroy       # To teardown everything
```

### 5. **Cloud Deployment**

**A. Set Cloud Provider Credentials**

Configure your AWS/GCP/Azure CLI and credentials as required.

**B. Deploy Infrastructure**

```bash
cd infra/terraform/aws    # or gcp/azure
terraform init
terraform apply           # Provisions managed K8s, DB, storage, etc.
```

**C. Deploy Application**

Update any cloud-specific variables in `.env`.
Push Docker images or trigger CICD pipeline (GitHub Actions/GitLab CI included).

### 6. **Using the Application**

- **Sign Up:** Create user and admin accounts via the dashboard.
- **Data Source:** Reddit comments and posts stream-in in real-time.
- **View Recommendations:** Personalized suggestions refresh as new data arrives.
- **Admin Dashboard:** View analytics, logs, feedback reports, A/B test results, model retraining status.

## ⚙️ Key Scripts & Commands

| Task                        | Script/Command                      |
|-----------------------------|-------------------------------------|
| Launch local stack          | `docker-compose up --build`         |
| Provision cloud infra       | `terraform apply` (per provider)    |
| Destroy infra               | `terraform destroy`                 |
| Run backend server locally  | `uvicorn api.main:app --reload`     |
| Run frontend locally        | `cd frontend && npm start`          |
| Trigger model training      | `python models/train.py`            |

## 📝 Documentation

See `docs/` for:
- Setup instructions with screenshots
- Data flow and architecture diagrams
- API and CLI usage
- Deployment/teardown guides for each environment

## 🧪 Testing & CI/CD

- Linting, tests, and deployments automated by `GitHub Actions`
- Code and model versioning via Git & MLflow
- MLOps: Drift, monitoring, automated retraining, rollback

## 🙋 Contributing

- Fork, branch, create PRs with clear titles
- All infra/scripts must be documented (usage + teardown)
- Issue tracker for bug reports and feature requests

## 📜 License

MIT (see LICENSE file)

**Questions?**  
Raise an issue or contact the repo maintainer for help!