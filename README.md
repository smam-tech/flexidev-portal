# FlexiDev - Portal/Frontend Application
## General information
* Purpose : Recruitment Process - Technical Test
* Company : Flexidev
* Position : DevOps Engineer
## How to Use
### Azure App Service + CI/CD
1. Quickstart a Azure App Service Web App using any sample container
2. Change the environments inside `.github\workflows\main.yml`

| Env Name | Description |
| --- | --- |
| IMAGE_TAG | Docker image tag, consisting of `ghcr.io/<github username>/<repo name>:<branch>` |
| APP_NAME | App name used in Azure App Service |
| SLOT_NAME | Slot name used in Azure App Service |

2. Change/Add the secrets by going to : repository web -> settings -> secrets and variables -> Actions

| Secret Name | Description |
| --- | --- |
| AzureAppService_PublishProfile_fd43a82d0f534adc8bf7728052df05fa | Your Azure Publish Profile, you can get it at the App Service Page` |
| GITHUB_TOKEN | This is auto generated, you don't need to specify this one unless necessary. |

3. The github action will do the rest for you and the CI/CD will run automatically.

### On-Premise Docker
1. Build the image using `docker build -t smam-tech/flexidev-portal`.
2. Run the image either using docker compose or docker run command `docker run -it -p 8080:80 --rm --name smam-flexidev-portal smam-tech/flexidev-portal`.
3. If you are using the docker run command, you can check the website on `localhost:8080`
## Architecture

![Architecture Diagram](https://github.com/smam-tech/flexidev-portal/blob/main/readme/img/Diagram.jpg?raw=true)

The architecture is quite straightforward, github will manage the code repository, image repository, and also the CI/CD while Azure will provide the place for deployment. The developer will have access to Github and push the code inside github, everytime changes happen then github actions will build the docker image and push it into github container registry then deploy it into Azure App Service

## Reference
* [Dockerize Vue](https://v2.vuejs.org/v2/cookbook/dockerize-vuejs-app.html?redirect=true)
* [Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/getting-started)