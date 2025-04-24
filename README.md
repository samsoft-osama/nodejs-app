# Backend Development EC2 Setup Guide

## Creating an Instance on AWS
- Create an EC2 instance through the AWS Management Console

## Connecting to Your Instance

Connect to your EC2 instance using SSH:

```bash
# Run this command to ensure your key is not publicly viewable
chmod 400 "first-deployment.pem"

# Connect to your instance using SSH
ssh -i "first-deployment.pem" ubuntu@ec2-51-21-255-227.eu-north-1.compute.amazonaws.com
```

## Setting Up the Environment

Install Node Version Manager (NVM):

```bash
# Install NVM
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash

# Load NVM into current shell
source ~/.bashrc

# Install the latest LTS version of Node.js
nvm install --lts

# Use the installed LTS version
nvm use --lts
```

## Deploying a Demo Node.js Project

Clone and set up the demo project:

```bash
# Clone the demo project repository
git clone https://github.com/yeshwanthlm/nodejs-on-ec2.git

# Navigate to the project directory
cd nodejs-on-ec2
```

## Setting Up PM2 Process Manager

Configure PM2 to manage your Node.js application:

```bash
# Start the application with PM2
pm2 start index.js

# Save the current PM2 process list
pm2 save

# Generate startup script
pm2 startup systemd
```

When prompted, copy and run the generated command:

```bash
# Example of the generated command
sudo env PATH=$PATH:/home/ubuntu/.nvm/versions/node/v22.15.0/bin /home/ubuntu/.nvm/versions/node/v22.15.0/lib/node_modules/pm2/bin/pm2 startup systemd -u ubuntu --hp /home/ubuntu
```

## Monitoring and Exiting

View application logs and exit:

```bash
# View application logs
pm2 logs

# Exit the SSH session when done
exit
```
