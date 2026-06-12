---
title: "Flash player ubuntu problem"
date: 2011-06-18
forum: General Help
---

### Post by uniku on 2011-06-18
Hi guys i have installed Ubuntu 10.10 2 days ago
I have an Pentium i3  2.4 with 1gb graphic card Nvidia Gt 420m 
I have done everything ok with updates and all was ok till the moment i went to  YouTube and then starts my problem....The videos as strarting slow i must wait 15 sec to start the video
On FaceBook the same when i play poker its not working its smth like freezing 
Thanks in advance ...

---

### Post by dragonfly41 on 2011-06-18
Try installing Flash-Aid as an addon to Firefox .. the launch button is then seen in top right panel of Firefox.

I have to say I'm also experiencing freezing on occasions.  
Ubuntu 10.10, Firefox 4.0.1

---

### Post by pqwoerituytrueiwoq on 2011-06-18
+1 flash aid
do you each have the latest graphics driver?
this is the ppa i use 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
however i got my nvidia driver at nvidia's website since lucid does not get the latest under nvidia-current

---

### Post by uniku on 2011-06-18
> **dragonfly41 said:**
> Try installing Flash-Aid as an addon to Firefox .. the launch button is then seen in top right panel of Firefox.

I have to say I'm also experiencing freezing on occasions.  
Ubuntu 10.10, Firefox 4.0.1

I have done what you said but still not working on facebook/poker
seems that on youtube is ok for the moment

---

### Post by uniku on 2011-06-18
> **pqwoerituytrueiwoq said:**
> +1 flash aid
do you each have the latest graphics driver?
this is the ppa i use 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
however i got my nvidia driver at nvidia's website since lucid does not get the latest under nvidia-current


I'm new on Linux so i'm not understanding what you mean exaclly
I have installed drivers from Nvidia those drivers that ubuntu found by himself

---

### Post by uniku on 2011-06-18
Sorry but even on youtube not working ....still i must wait again :S

---

### Post by pqwoerituytrueiwoq on 2011-06-18
> **uniku said:**
> I'm new on Linux so i'm not understanding what you mean exaclly
I have installed drivers from Nvidia those drivers that ubuntu found by himself
basically these commands in a terminal
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```
now the update manager should open

---

### Post by uniku on 2011-06-18
[FONT=monospace]iri@ubuntu:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
miri@ubuntu:~$ ^C
miri@ubuntu:~$ 


i've done even update but notthing happent i think 
[/FONT]

---

### Post by uniku on 2011-06-18
SOLVED thanks 2 all you guys :D
Now i have everything ok :D:D 
Thanks alllllllll :D

---

### Post by pqwoerituytrueiwoq on 2011-06-18
> **uniku said:**
> SOLVED thanks 2 all you guys :D
Now i have everything ok :D:D 
Thanks alllllllll :D
then mark the thread as solved (look under thread tools at the top of the page)
i forgot to mention to restart gdm or reboot i take it you restarted and it suddenly worked after installing updates

---

