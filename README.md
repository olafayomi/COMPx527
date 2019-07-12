## COMPX527 Assignment

### Requirements
* Apply to join [AWS Educate](https://aws.amazon.com/education/awseducate/) to get free AWS credit.


### Objectives
* You are required to compose a cloud-based solution using AWS services.
* You will perform a live demo and presentation of your solution.
* The goal of this assignment is to give hands-on experience of using cloud services and how to design and deploy cloud-native applications. In order to achieve this objective, your cloud-based solution will be assessed based on these criteria:
  * Deployment: How will your solution be deployed on AWS or cloud service provider of choice ?
  * Automation: Is the deployment process automated or manual ?
  * Reproduciblity: Can your solution be easily replicated or deployed elsewhere or by someone else ?
  * Scalability: Has consideration been given to how to scale up or scale down your solution to meet increasing demand ?
  
You are expected to use tools like [ansible](https://www.ansible.com/resources/get-started),[terraform](https://www.terraform.io/) and [AWS CloudFormation](https://aws.amazon.com/cloudformation/) to achieve these objectives. This will require that you get comfortable with the [AWS CLI](https://aws.amazon.com/cli/). See instructions below on installing AWS CLI and ansible to give you an idea of how to proceed with your assignment.

### Getting started with AWS CLI and Ansible
The installation was performed on a Linux workstation, the instructions and commands might be different for other operating systems. Check the links below for instructions on how to install AWS CLI on Windows and MAC:
* https://docs.aws.amazon.com/cli/latest/userguide/install-windows.html
* https://docs.aws.amazon.com/cli/latest/userguide/install-macos.html

For linux:
* Install python3-pip 
```
sudo apt-get install python3-pip
```
* Install a python virtual environment
```
pip3 install virtualenv
```
* Create a virtualenv for your project
```
virtualenv -p /usr/bin/python3 COMP527-ASSGMNT1
```
* Activate your virtualenv
```
source COMP527-ASSGMNT1/bin/activate
```
* Install AWS CLI inside your virtualenv
```
(COMP527-ASSGMNT1) root@ubuntu:~# pip3 install awscli
```
* Follow these [instructions](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) to generate AWS credentiails

* Configure AWS CLI with your AWS credentials to interact with AWS services via the command line.
```
(COMP527-ASSGMNT1) root@ubuntu:~# aws configure 
  AWS Access Key ID [None]: **********************
  AWS Secret Access Key [None]: ************************************** 
  Default region name [None]: ap-southeast-2 
  Default output format [None]: json
```
* Confirm your credentials work by creating and deleting test AWS s3 buckets for example
```
(COMP527-ASSGMNT1) root@ubuntu:~# aws s3 mb s3://comp527-assgnmt
(COMP527-ASSGMNT1) root@ubuntu:~# aws s3 rb s3://comp527-assgnmt
```
* Install ansible in the virtualenv to automate the deployment of your solution.
```
pip install ansible
pip install boto3
pip install botocore
```
* An example: ansible-playbook to deploy a simple website on s3. (remember to change your bucket name in the ansible playbook)
```
## Remember to change the bucket name and blog_root_dir in
## ansible-s3/roles/deploy-comp527-s3/defaults/main.yml to your own.
git clone git@github.com:olafayomi/COMPx527.git
cd COMPx527/ansible-s3
ansible-playbook main.yml --tags deploy-live-s3 
```
* Your website should be live at: http://your-bucket-name.live.s3-website-ap-southeast-2.amazonaws.com/index.html)

*credits:
 http://deploy.live/blog/aws-s3-hosted-blog-using-jekyll-and-ansible/

