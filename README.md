# Jenkins Installations on RedHat Linux
#!/bin/bash

# Installing Jenkins on RHEL 7/8, CentOS 7/8 or Amazon Linux OS
# You can execute this script as user-data when launching your EC2 VM.
sudo timedatectl set-timezone America/New_York
sudo hostnamectl set-hostname jenkins
sudo yum install wget -y
sudo wget -O /etc/yum.repos.d/jenkins.repo \
     https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade -y
# Add required dependencies for the jenkins package
sudo yum install java-11-openjdk -y
sudo yum install jenkins -y
sudo systemctl daemon-reload
# start jenkins
# Start Jenkins
# You can enable the Jenkins service to start at boot with the command:
sudo systemctl enable jenkins
#You can start the Jenkins service with the command:=
sudo systemctl start jenkins
# You can check the status of the Jenkins service using the command:
sudo systemctl status jenkins
sudo su - ec2-user
echo "echo of jenkins installation"

To generate password for the jenkins GUI:
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Then copy and paste on password....

cat /etc/passwd
you will find that the jenkins user has a 'false' as an interpreter instead of the shell being /bin/bash, it is /bin/false. To change this, vi or vim or nano into /etc/passwd and change the line element of 'false' to 'bash' to have the appropriate interpreter for jenkins user.

Jenkins is run as a jenkins user and not as root user
