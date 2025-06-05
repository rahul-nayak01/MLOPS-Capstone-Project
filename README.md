# MLOPS-Capstone-Project
🚀 ML Project: End-to-End MLOps Pipeline with EKS Deployment
🔧 Setting Up Project Structure
Create a GitHub repository and clone it locally.

Create a virtual environment using conda: atlas with Python 3.10.

Activate the environment.

Install Cookiecutter.

Use the DrivenData cookiecutter template.

Rename src.models to src.model.

Add, commit, and push changes to GitHub.

⚙️ Setting up MLFlow with Dagshub
Visit Dagshub dashboard.

Create a new repo > Connect GitHub repo > Select and Connect.

Copy MLFlow tracking URL and snippet.

Install dagshub and mlflow.

Run experiment notebooks.

Commit and push changes.

📦 DVC Setup
Initialize DVC.

Create a temporary local folder named local_s3.

Add it as a DVC remote: mylocal.

Add the following scripts inside src:

logger

data_ingestion.py

data_preprocessing.py

feature_engineering.py

model_building.py

model_evaluation.py

register_model.py

Add dvc.yaml (till model evaluation metrics).

Add params.yaml.

Run DVC pipeline using dvc repro.

Check status with dvc status.

Commit and push all updates.

☁️ Setup S3 Remote Storage
Create an IAM user and S3 bucket.

Install dvc[s3] and awscli.

(Optional) List or remove remotes.

Configure AWS credentials using aws configure.

Add your S3 bucket as a DVC remote: myremote.

🌐 Flask App & CI Setup
Create a directory flask_app and add necessary files.

Install flask and run the app. Use dvc push to upload data to S3.

Freeze dependencies to requirements.txt.

Add GitHub Actions CI file: .github/workflows/ci.yaml.

Generate Dagshub token > Add it to GitHub secrets and CI workflow.

✅ Testing
Create directories tests and scripts for CI test scripts.

🐳 Docker Setup
Install pipreqs and generate requirements inside flask_app.

Add a Dockerfile. Start Docker Desktop.

Build Docker image: capstone-app:latest.

Run using port 5000 and provide env variable CAPSTONE_TEST.

(Optional) Push image to Docker Hub and test pull-run.

🔐 AWS Environment Variables
AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

AWS_REGION

ECR_REPOSITORY

AWS_ACCOUNT_ID

Permissions: AmazonEC2ContainerRegistryFullAccess

🔄 CICD with ECR
Update CI pipeline to build and push image to ECR.

☸️ EKS Setup (Kubernetes)
Pre-steps
Remove conflicting AWS CLI (Python-based) if using Anaconda.

Set proper PATH to .msi installed AWS CLI.

Verify AWS CLI, kubectl, and eksctl installations.

Install Tools
Download and move kubectl and eksctl to C:\Windows\System32.

Validate installation with version commands.

EKS Cluster Creation
Create EKS cluster using eksctl.

Update kubectl config for EKS.

List clusters and verify cluster config.

(Optional) Delete EKS cluster.

Verify cluster status and connectivity: kubectl get nodes.

Check namespaces, pods, and services.

Deploy app to EKS via CI pipeline.

🌐 External Access
Once the service is exposed via LoadBalancer, run:

kubectl get svc flask-app-service

Access the app via external-ip:5000 in browser or terminal.

📊 Prometheus Monitoring Setup
Launch Ubuntu EC2 instance (t3.medium, 20GB).

SSH into instance.

Update packages.

Download and extract Prometheus.

Move Prometheus files to standard paths.

Edit prometheus.yml to monitor the Flask app.

Verify Prometheus binary path.

Run Prometheus with the updated config.

📈 Grafana Setup
Launch another Ubuntu EC2 instance (t3.medium, 20GB).

SSH into instance.

Update packages.

Download Grafana .deb package.

Install and start Grafana.

Enable it to start on boot and verify its status.

Access Grafana UI at http://<public-ip>:3000 (admin/admin).

Add Prometheus as a data source.

🧹 AWS Resource Cleanup
Delete deployment, service, secrets using kubectl delete.

Delete EKS cluster using eksctl delete cluster.

Verify cluster deletion.

(Optional) Delete ECR and S3 artifacts.

Confirm with AWS support if necessary.

