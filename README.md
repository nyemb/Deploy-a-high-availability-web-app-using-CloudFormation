## Deploy a High Availability web app using CloudFormation

## In this repo
### network.yml
Template containing all the network resources to be deployed. Deploy this first.

### servers.yml
Template containing all the app resources to be deployed. Deploy this after deploying the network resources.

### network-parameters.json
Parameters that you can tweak to customise:
- <strong>EnvironmentName</strong>: The EnvironmentName you want to use for the deployment
- <strong>VpcCIDR</strong>: The CIDR of your VPC
- <strong>PublicSubnet1CIDR/PublicSubnet2CIDR/PrivateSubnet1CIDR/PrivateSubnet2CIDR</strong>: The - CIDR of your public and private subnets
### server-parameters.json
parameters for the server
### infrastructure_diagram.png
The infrastructure Diagram
![Infrastructure diagram](infrastructure_diagram.png)

## Prerequisites
A user account with programmatic access to AWS

## To run

Create network stack using the following command:  
`aws cloudformation create-stack --stack-name NetworkStack --template-body network.yml --parameters network-parameters.json`  

Wait a few minutes for the stack creation to complete. Check the status with `aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE` 

Create the server stack:  
`aws cloudformation create-stack --stack-name ServerStack --template-body servers.yml --parameters server-parameters.json.json`  


## Output
