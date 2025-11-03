# Azure Project: Static Website + Azure Container Instance Integration
# Team Members
  1.	M. Sanjana – Development and Deployment 
  2.	Yeshwanth Veeresham – Data Collection and Information Gathering
  3.	Khadar – Documentation
Project Overview
This project demonstrates the deployment of a modern static website using Azure Storage and its integration with a live Azure Container Instance (ACI) running a demo Nginx container. It showcases the combination of static and dynamic content hosted entirely in the Azure Cloud, without the need to manage any virtual machines.

The static website (HTML + CSS) is hosted using Azure Storage Static Website Hosting, while the dynamic component (Nginx container) runs on Azure Container Instances. A button on the static site links directly to the container endpoint, offering an interactive and cloud-native demonstration.
Problem Statement
Modern web applications often require both static content (HTML, CSS, JS) and dynamic backend services (APIs, containers, etc.). Traditionally, these are hosted on virtual machines or managed web servers, which involve configuration overhead, scalability challenges, and maintenance costs.

The goal is to create a fully serverless, scalable, and cost-effective solution that:

•	Hosts a static website efficiently.
•	Integrates seamlessly with a running containerized service.
•	Minimizes infrastructure management.
•	Demonstrates Azure’s scalability and simplicity for modern web solutions.
Project Goals
•	Deploy a static website using Azure Storage.
•	Launch a dynamic service using Azure Container Instances (Nginx demo).
•	Link static and dynamic content through a live integration.
•	Use Azure CLI for end-to-end automation of deployment steps.
•	Demonstrate a serverless web architecture (no VMs, minimal setup).
•	Ensure scalability, reliability, and easy maintenance through Azure-native tools.
Technologies and Azure Services Used
Technologies Used
•	HTML & CSS — Designing and styling the static web pages.
•	Nginx — Containerized web server for demo purposes.
•	Azure CLI — Command-line tool for managing Azure resources.
•	Bash Shell — Used for scripting and automation of deployment.
Azure Services Used
Service	Purpose
Azure Resource Group	Logical container for organizing and managing related project resources.
Azure Container Instances (ACI)	Runs the Nginx container dynamically without the need for virtual machines.
Azure Storage Account	Stores and serves static website files.
Azure Static Website Hosting	Enables hosting of HTML and CSS files directly from Azure Storage.
Azure DNS (via DNS Name Label)	Provides a public URL to access the running container.
Project Steps

Step 1: Create a Resource Group
az group create --name MyNewResourceGroup --location centralindia
Step 2: Create a Storage Account
az storage account create --name mystaticweb12345 --resource-group MyNewResourceGroup --location centralindia --sku Standard_LRS
Step 3: Enable Static Website Hosting
az storage blob service-properties update --account-name mystaticweb12345 --static-website --index-document index.html
Step 4: Create Your Static Website
mkdir -p ~/my-static-site
cat << 'EOF' > ~/my-static-site/index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Azure Static Web App</title>
  <link href="style.css" rel="stylesheet">
</head>
<body>
  <header>
    <h1>Welcome to My Azure Static Web App</h1>
    <p>Hosted using Azure Storage and Azure Container Instances</p>
  </header>
  <main>
    <a href="http://mywebapp-demo12345.centralindia.azurecontainer.io" target="_blank" class="demo-button">Visit My Container App</a>
  </main>
  <footer>
    <p>© 2025 MyAzureWebProject | Powered by Azure</p>
  </footer>
</body>
</html>
EOF
Step 5: Upload Website Files
az storage blob upload-batch --account-name mystaticweb12345 --source ~/my-static-site --destination '$web'
Step 6: Get Static Website URL
az storage account show --name mystaticweb12345 --query "primaryEndpoints.web" --output tsv
Step 7: Deploy a Container App
az container create --resource-group MyNewResourceGroup --name mywebapp-container --image mcr.microsoft.com/azure-cli --cpu 1 --memory 1 --dns-name-label mywebapp-demo12345 --os-type Linux --location centralindia
Step 8: Get Container Public URL
az container show --resource-group MyNewResourceGroup --name mywebapp-container --query "ipAddress.fqdn" --output tsv






# Project websites
  GitHub:-https://github.com/sanjana0511?tab=repositories
  Youtube:- https://youtu.be/8YQ1Kn6lHQs?si=MvkkXAep_5C96_J-
  Website:-https://mystaticweb12345.z29.web.core.windows.net/


  
# ScreenShot
**WhatsApp Image 2025-10-10 at 13.05.52.jpeg**
**WhatsApp Image 2025-10-10 at 13.03.06.jpeg**
**WhatsApp Image 2025-10-10 at 13.01.48.jpeg**
**WhatsApp Image 2025-10-10 at 13.00.56.jpeg**
**WhatsApp Image 2025-10-10 at 12.59.39.jpeg**
**WhatsApp Image 2025-10-10 at 12.57.15.jpeg**
**WhatsApp Image 2025-10-10 at 12.48.10.jpeg**
**WhatsApp Image 2025-10-10 at 12.45.12.jpeg**
**WhatsApp Image 2025-10-10 at 11.38.32.jpeg**
