# End-to-End-CICD-Pipeline
End to End CICD Pipeline using Azure DevOps and Argo CD.

**Continuous Integration:**
-Code Analysis: SonarQube server inspects the code quality.
-Build image: Builds a Docker image from a specified Dockerfile.
-Image Scan: Installs Trivy to scan the image for vulnerabilities.
-Push: Pushes the Docker image to Azure Container Registry (ACR).
-Publish Artifacts: Uploads the scan results to an artifact staging directory.
-Update: Executes a script to dynamically update the image tag in the Kubernetes manifest file.

**Continuous Deployment:**
Automated deployment process by integrating Argo CD with the source code repository to monitor the Kubernetes manifests folder. When the image tag is updated in the deployment file within this folder, Argo CD automatically pulls the new image from ACR and deploys it to the Azure Kubernetes Service (AKS) cluster.

-Integrated Azure Key Vault to securely store and retrieve secrets.
-Used Terraform to provision various Azure resources.
-Used virtual machine scale sets for auto scaling agents.
