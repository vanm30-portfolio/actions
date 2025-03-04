# Actions
Welcome to the `actions` repository under `vanm30-portfolio`! This project serves as a centralized hub for common CI/CD workflows and reusable automation scripts. It’s designed to streamline development/deployment processes  across multiple projects within the `vanm30-portfolio` project — and beyond, since it’s open source! For now, it provides foundational workflows (like deployment), with plans to expand into more utilities in the future.

## Purpose
The goal of this repo is to house shared tools and CI/CD pipelines. 

## Current Features
* Deployment Workflow: A basic reusable workflow for building docker image, deploying image on a server and running docker cotainer (see `deploy.yml`).

## Usage
To use the workflows in your own project, reference them in your project-specific GitHub Actions workflow files. Below is an example of how to integrate the `deploy.yml` workflow.

### Example
1. **Create a Workflow in Your Project**

In your repo (e.g., `yourname/my-project`), add a file like `.github/workflows/deploy-project.yml`:
```
name: Deploy Project
   on:
     create:
       tags:
         - v*  # Triggers on tags like v1.0, v2.3.1
   jobs:
     deploy:
       uses: vanm30-portfolio/actions/.github/workflows/deploy.yml@main
```

2. **Set Up Secrets**
The  workflow mostly require secrets (e.g., `SERVER_IP`, `SSH_USER`).
Add these to your repo’s settings under Settings > Secrets and variables > Actions or at the org level.
Please check respective code and analyze all secrets to use in your project.

3. **Push and Run**
Create a tag (e.g., `git tag v1.0 && git push origin v1.0`).
Check the Actions tab to see it in action!

## Future Plans
Expect more workflows and tools, such as:
Test automation (e.g., linting, unit tests).
Build scripts for common frameworks.
Other CI/CD goodies

## Contributing
Fork and suggest improvements via pull requests.
Open issues for bugs or feature requests.
Keep it simple and reusable!
