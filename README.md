Kubernetes Solo Environment
===========================


Install Dependencies (Ubuntu)
-----------------------------

### VirtualBox

From [documentation](https://www.virtualbox.org/wiki/Linux_Downloads) page:

```bash
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
apt-key fingerprint 98AB5139
        pub   1024D/98AB5139 2010-05-18
            Key fingerprint = 7B0F AB3A 13B9 0743 5925  D9C9 5442 2A4B 98AB 5139
        uid                  Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>
        sub   2048g/281DDC4B 2010-05-18

wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
apt-key fingerprint 2980AECF
        pub   4096R/2980AECF 2016-04-22
            Key fingerprint = B9F8 D658 297A F3EF C18D  5CDF A2F6 83C5 2980 AECF
        uid                  Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>
        sub   4096R/920E471F 2016-04-22

sudo apt-add-repository "deb http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib"
sudo apt-get update
sudo apt-get install virtualbox-5.2 dkms
```

### Vagrant (2.2.5)

From [download](https://www.vagrantup.com/downloads.html) page:

```bash
wget 'https://releases.hashicorp.com/vagrant/2.2.5/vagrant_2.2.5_x86_64.deb'
sudo dpkg -i vagrant_2.2.5_x86_64.deb
```

### Ansible

Install dependencies (python, pip and virtualenv):

```bash
sudo apt-get install python-pip
sudo pip install -U pip
sudo pip install virtualenv
```

Install ansible and *kubernetes solo* role:

```bash
# Create python virtual environment
virtualenv -p /usr/bin/python3 venv
# Activate python virtual environment
source venv/bin/activate
# Install dependencies
pip install -r requirements.txt
# Install `kubernets solo` ansible role
ansible-galaxy install tandiljuan.kubernetes_solo
# Work with ansible, provision and when you don't need to use it anymore, just
# exit (deactivate) the virtual environment.
```


Run environment
---------------

Once all dependencies are installed, run (setup) local *kubernetes solo* environment with the following command:

```bash
vagrant up
```
