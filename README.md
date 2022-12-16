#### Set up of a real time production scenario of various Linux hosts (distros) which can be managed centrally with Ansible Master. <br/><br/>

* Instal virtual box and download latest versions (64bit) of Debian, Ubuntu & Cent OS VDI's from [OS Box images for virtual box](https://www.osboxes.org/virtualbox-images/).<br/>
* [Follow the steps to install a host for each distro (debian, centos & ubuntu](https://www.youtube.com/watch?v=pIKFxK2Gfnc). <br/>
* Follow the steps carefully to ensure internet access for all the VDI's. Ubuntu and Debian would work fine but CentOS can give issues and [this video will resolve the problem](https://www.youtube.com/watch?v=IxookDRgOZM).<br/>
* For CentOS download the "Workstation" (not the server). <br/>
* Password would be in the info tab. <br/>
  ![image](https://user-images.githubusercontent.com/92582005/208136867-87caf7e4-2a5f-4be1-a595-79d2ac220ba1.png) <br/>
* Start the servers and SSH into them through MobaXterm. <br/>
* [Make any one of the server as Ansible master and install Ansible.](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html). Verify by running the command "ansible --version".<br/>
* In Ansible master create any folder (e.g. ansible_test) and change directory to it (mkdir ansible_test & cd ansible_test). <br/>
* Create file ansible.cfg and enter the below two commands. <br/>
  $ nano ansible.cfg <br/>
  ![image](https://user-images.githubusercontent.com/92582005/208138868-12cabb61-3000-4c94-9ea0-b54a11e56eef.png) <br/>
* Group your remote hosts as per OS and enter the login credentials in the ":vars" section as below. Change the IP addresses with your's. For sudo user password add "ansible_become_password".<br/>
  ![image](https://user-images.githubusercontent.com/92582005/208139334-46812457-afc2-4931-b9d9-a90699aa44b9.png)<br/>
* To check connectivity run the playbook ping_test.yaml with below command & the output will be similar to image below. Source code uploaded in this repository.<br/>
  $ ansible-playbook ping_test.yaml <br/>
  ![image](https://user-images.githubusercontent.com/92582005/208140659-e4268175-6aab-48b0-9b44-a8edcb32eee0.png) <br/>
* Connectivity can also be checked by running the below adhoc command and output would be like image below. <br/>
  ![image](https://user-images.githubusercontent.com/92582005/208140985-8fedc77d-18e5-4462-8b62-d5cd151ded9b.png) <br/>
* To check OS releases of each remote hosts run the below ansible playbook and output will be similar to the image below (playbook source code uploaded). <br/>
  $ ansible-playbook os-release1.yaml
  ![image](https://user-images.githubusercontent.com/92582005/208141323-ea01b920-f23f-4cf1-9d93-ad0dab9fb98c.png) <br/>
* OS release can also be checked by running the below adhoc command and the output will be as the image. <br/>
  $ ansible all -a "cat /etc/os-release" <br/>
  ![image](https://user-images.githubusercontent.com/92582005/208141930-703fad0e-8e51-49c7-b900-05ba0830765c.png) <br/><br/>

* The real time lab is not set up. The machines can be shut down from virtual box and restarted anytime later. More ansible automation tasks can be performed in setup. <br/>
