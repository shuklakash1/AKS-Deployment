# AKS-Deployment
# AKS Deployment
# Deployment process of a MERN application using AKS

Need the following installation before starting the project:
- Azure Account: An active Azure subscription.

- Azure CLI: Installed on your local machine.

- Docker: Installed and running on your local machine.

- Kubectl: Installed on your local machine.


# Cloning the repository into the local system:
command: git clone (add repo link here)

# Containerize the Application
- Create docker files for backend and frontend.

- ![Screenshot 2024-06-01 230033](https://github.com/shuklakash1/AKS-Deployment/assets/46483575/38fc50c1-3a25-4e69-8c43-56c2f32be69d)



- Building the Docker Images.

    command: docker build -t <your-image-name> .


- Push the Docker Image to a Registry.

    command: docker login
             docker tag <your-image-name>:<version> <your-dockerhub-username/registory-name>:<version>
             docker push <your-dockerhub-username/registory-name>:<version>

# Set Up AKS
-  Add Resource Groups in Azure portal.

    Microsoft.Compute
    microsoft.insights
    Microsoft.ContainerInstance
    Microsoft.ContainerRegistry
    Microsoft.ContainerService
    Microsoft.Kubernetes
    Microsoft.KubernetesConfiguration
    Microsoft.KubernetesRuntime

   ![Screenshot 2024-06-02 140705](https://github.com/shuklakash1/AKS-Deployment/assets/46483575/8663b11c-b8f9-4e99-b373-22c0a47061e4)


- Resource group:

  ![Screenshot 2024-06-03 212128](https://github.com/shuklakash1/AKS-Deployment/assets/46483575/806a5392-e2f7-4d57-a246-da3f1b790c63)


- Kubernetes:

  ![Screenshot 2024-06-03 212057](https://github.com/shuklakash1/AKS-Deployment/assets/46483575/c7cc1952-7022-47c6-9830-54a934b6db5e)


- Login with azure in your terminal

    command: az login

    ![Screenshot 2024-06-01 230904](https://github.com/shuklakash1/AKS-Deployment/assets/46483575/c7475906-2bcb-4c1c-bc3a-bebb63c49edd)
  

- Creation of an AKS Cluster

    command: az aks create --resource-group mern_micro_app --name mern_cluster --node-count 2 --enable-addons monitoring --generate-ssh-keys

- Get AKS Credentials

    command: az aks get-credentials --resource-group mern_micro_app --name mern_cluster

    ![Screenshot 2024-06-03 212222](https://github.com/shuklakash1/AKS-Deployment/assets/46483575/2b6ab466-7cf9-49da-b5c9-c7268c317c8b)

Installation of Ingress
    command: kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml

  ![Screenshot 2024-06-03 212254](https://github.com/shuklakash1/AKS-Deployment/assets/46483575/02c43206-a7d5-40f9-8a2b-c1bab1942fa2)


Create & execute K8 deployment files and service files of frontend and backend:
    command: kubectl apply -f backend-deployment.yaml # put your file name 
             kubectl apply -f backend-service.yaml # put your file name 
             kubectl apply -f frontend-deployment.yaml # put your file name 
             kubectl apply -f frontend-service.yaml # put your file name 

   ![Screenshot 2024-06-03 213346](https://github.com/shuklakash1/AKS-Deployment/assets/46483575/a4c14f14-3e48-459e-8748-d80753d56aa7)

   

Check Pods:
    command: kubectl get pods

  ![Screenshot 2024-06-03 221132](https://github.com/shuklakash1/AKS-Deployment/assets/46483575/17fbe9f9-c765-4d28-83ca-84fed267e892)


Check svc:
    command: kubectl get svc

  ![Screenshot 2024-06-03 221149](https://github.com/shuklakash1/AKS-Deployment/assets/46483575/bc9b72d2-ab1b-478b-aaad-6020921e9db0)


Create an ingress file and excute that file:
    command: kubectl apply -f ingress.yaml # put your file name 
alt text

Check get ingress:
    command: kubectl gbet ingress
alt text

Setup DNS:
alt text

Now check your frontend and backend with your domain name:
Frontend:

alt text

Backend:

- Hello Service:
alt text

- Profile Service:
alt text
