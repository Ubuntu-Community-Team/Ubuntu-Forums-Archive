---
title: "ssh setup"
date: 2010-09-23
forum: General Help
---

### Post by noteasy_thatsbs_d on 2010-09-23
I am new to ubuntu but not unix. I have a lot of experience with redhat (CentOS).

I am trying to setup ssh access to my Ubuntu 10 vm and am running into some problems

I can access the outside from the server ping google.com and I can ping the server from a public IP. I know ssh works as I can ssh localhost from the console and connect successfully. I have a gateway vyatta on linux box, although no extra config was necessary to allow ssh to my ESX kernel. I am just wondering if there is something I didn't setup on the Ubuntu server. I did #sudo ufw disable and still cannot connect. When I try to putty in with ssh I don't get "connection refused" I get "connection timed out" 

Any thoughts?

---

### Post by CharlesA on 2010-09-23
SSH isn't installed by default on Ubuntu (it is on CentOS).

Install it by running this from a terminal:

```
sudo apt-get install ssh
```

If it's already installed, post the output of:

```
ifconfig
```
```
netstat -ln
```

---

### Post by perspectoff on 2010-09-23
> **CharlesA said:**
> SSH isn't installed by default on Ubuntu (it is on CentOS).

Install it by running this from a terminal:

```
sudo apt-get install ssh
```

If it's already installed, post the output of:

```
ifconfig
```
```
netstat -ln
```

SSH (which is the ssh client) is installed by default on all my Ubuntu machines (even on the LiveCD) -- I don't don't why it isn't on yours, Charles.

But the OpenSSH server is not.

 sudo apt-get install openssh-server

---

### Post by noteasy_thatsbs_d on 2010-09-23
after installing vmWare tools I am able to connect. Guess it was a driver issue.

Thanks for the input.

---

### Post by CharlesA on 2010-09-23
> **perspectoff said:**
> SSH (which is the ssh client) is installed by default on all my Ubuntu machines (even on the LiveCD) -- I don't don't why it isn't on yours, Charles.

But the OpenSSH server is not.

 sudo apt-get install openssh-server

Correct, the client is installed by default, but the server isn't.

Running the **apt-get install ssh** command installs openssh-server, since the client is already installed:

```
ubuntu@ubuntu-laptop:~$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openssh-server
The following NEW packages will be installed:
  openssh-server ssh
0 upgraded, 2 newly installed, 0 to remove and 8 not upgraded.
Need to get 286kB of archives.
After this operation, 823kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

Less typing is a good thing.

---

