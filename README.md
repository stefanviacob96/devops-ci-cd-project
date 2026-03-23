DevOps CI/CD Docker Project

This project demonstrates a CI/CD pipeline that automatically builds, tests, and deploys a containerized web application.

When code is pushed to the main branch, the system:

Builds a Docker image
Tests the application automatically
Publishes the image to GitHub Container Registry (GHCR)
Deploys the new version to a Linux server

This simulates a real-world DevOps workflow where applications are updated automatically after each change.

Technologies Used
Docker
Docker Compose
GitHub Actions (CI/CD)
Python (Flask)
GitHub Container Registry (GHCR)
Linux server (Multipass VM)
Self-hosted GitHub Actions runner
How the System Works
Developer pushes code to main
        │
        ▼
GitHub Actions builds and tests the app
        │
        ▼
Docker image is pushed to GHCR
        │
        ▼
Deployment process is triggered
        │
        ▼
Server pulls the new image
        │
        ▼
Docker Compose restarts the container

Result: the server runs the latest version of the application.

CI/CD Workflows
1) Build, Test, Push Image (CI)

Runs on every push to main:

Build Docker image
Run container
Perform HTTP smoke test
Push image to GHCR
2) Deployment (CD)

The deployment stage was tested using a Linux server (Multipass VM).

Server setup included:

Docker
Docker Compose
Self-hosted GitHub Actions runner

Deployment process:

docker compose pull
docker compose up -d --force-recreate

This ensures the server always runs the latest version of the application.

Important Note

The server is not kept running permanently to avoid unnecessary resource usage.

The deployment process has been fully tested and can be reproduced at any time using the steps described above.

Run Locally

Build and run the application:

docker build -t devops-ci-app .
docker run -p 5000:5000 devops-ci-app

Open in browser:

http://localhost:5000
Project Goals
CI/CD pipeline design
Automated Docker image builds
Automated testing in pipelines
Container registry integration
Deployment to a Linux server
Self-hosted GitHub Actions runners
