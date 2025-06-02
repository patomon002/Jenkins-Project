🛠️ CI/CD Pipeline for Maven Web Application (Jenkins + Docker + SonarQube + Nexus)

This project defines a Jenkins Declarative Pipeline for automating the build, test, quality check, artifact upload, containerization, and deployment of a Maven-based Java web application. It integrates with SonarQube for code analysis, Nexus for artifact storage, and Docker for containerized deployment.

📁 Project Repository

The application source is pulled from:
https://github.com/patomon002/maven-web-application

🔧 Pipeline Overview

This Jenkins pipeline consists of the following stages:

1. 🧬 GitClone
Clones the latest version of the application from GitHub.
2. 🧪 Test + Build
Runs unit tests.
Builds the project using mvn clean package.
3. 🧠 Code Quality
Analyzes the code using SonarQube (mvn sonar:sonar).
4. 🧳 Upload Artifacts
Deploys the packaged artifacts to a Nexus Repository using mvn deploy.
5. 🐳 Pre-deployment
Builds a Docker image for the application.
Pushes the image to Docker Hub (patomon002/maven-web-app).
⚠️ Ensure the Jenkins node has Docker installed and Docker socket access (/var/run/docker.sock).
6. 🔥 Undeploy
Removes any existing Docker container named webapp.
7. 🚀 Deployment
Deploys the application in a Docker container on port 8000.
8. 📬 Email Notification
Sends a basic echo notification after successful deployment (can be extended to actual email).
💡 Requirements

Ensure the Jenkins environment has:

Docker installed and properly configured.
Docker Pipeline plugin installed.
Maven configured (tool name: Maven in Jenkins).
SonarQube and Nexus credentials set up in settings.xml or Jenkins credentials.
A Jenkins agent labeled Node1 with access to Docker.
📦 Docker Image

Docker image built and pushed:
📦 patomon002/maven-web-app

Run manually (if needed):

docker run -d -p 8000:8080 --name webapp patomon002/maven-web-app
📧 Notifications

The final stage echoes a message. Integrate email notifications using the Email Extension Plugin if needed.

📌 Notes

This pipeline demonstrates an end-to-end CI/CD workflow.
Suitable for DevOps testing, training, and deployment automation practice.
Modify according to your infrastructure and credentials management.
🧑‍💻 Author

Patrick Omorovan
