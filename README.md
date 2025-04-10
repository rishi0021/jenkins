# jenkins

1. create a EC2 instance
2. connect to instance
3. install java
   sudo apt update
  sudo apt install openjdk-17-jre
4. curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
 
5. run the command ps -ef |grep jenkins (this will give you on which port jenkins is running )
6. Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.
7. go to security group add inbound traffc at port 8080(jenkins is running on this port)
8. go to browser type a url : http:/"ec2_ip_address:port_number"
9. ![image](https://github.com/user-attachments/assets/baea84c6-7fce-4363-94cb-069c13fa90ea)
10. you will get the login page for jenkins
11. get the password from "/var/lib/jenkins/secrets/initialAdminPassword"
12. select install suggested plugins
13. fill the form -> start jenkins
14. install docker -sudo apt install docker.io
15. grant access to ubuntu and jenkins
    sudo su - 
    usermod -aG docker jenkins
    usermod -aG docker ubuntu
    systemctl restart docker
16. type a command to check if docker is creating contaninner "docker run hello-world"    
17. switch user as jenkins
18. got to jenkin on web browser
19. dashboard ->manage jenkins ->plugins -> available plugins
20. search for docker pipeline and install
21. restart jenkins on browser
22. new item -> enter project name ->pipeline
23. change defination to pipeline scripts from scm
24. add the git repo "https://github.com/iam-veeramalla/Jenkins-Zero-To-Hero/blob/main/python-jenkins-argocd-k8s/Jenkinsfile"
