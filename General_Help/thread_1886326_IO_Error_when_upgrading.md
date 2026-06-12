---
title: "I/O Error when upgrading"
date: 2011-11-24
forum: General Help
---

### Post by Kaze105 on 2011-11-24
After doing a fresh install of Ubuntu, I tried to install all the update in update manager. All of them seemed to update just fine, but one update seemed to have a problem  -  Assistive Technology Service Provider Interface - Python bindigs   : python-pyatspi2.

After restarting the computer and using the terminal. (Sudo apt-get update, sudo apt-get upgrade) I get the following error: 

```
kaze105@kaze105-M860TU:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python-pyatspi2
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.7 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main python-pyatspi2 all 2.2.1-0ubuntu1 [33.7 kB]
Fetched 33.7 kB in 2s (12.9 kB/s)          
(Reading database ... 162226 files and directories currently installed.)
Preparing to replace python-pyatspi2 2.2.0-0ubuntu1 (using .../python-pyatspi2_2.2.1-0ubuntu1_all.deb) ...
Unpacking replacement python-pyatspi2 ...
dpkg: error processing /var/cache/apt/archives/python-pyatspi2_2.2.1-0ubuntu1_all.deb (--unpack):
 unable to stat `./usr/lib/python2.7/dist-packages/pyatspi/role.py' (which I was about to install): Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/python-pyatspi2_2.2.1-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Tried to google for any solutions, but I a few things I tried didnt work. Any help would be much appreciated.

---

### Post by Rubi1200 on 2011-11-24
Hi and welcome to the forums :-)

Try these commands:

```
sudo apt-get install -f 
sudo dpkg --configure -a
sudo apt-get update
```

Post back with error messages.

---

### Post by Kaze105 on 2012-01-25
Sorry for posting after so long.  I get the same error when I enter   sudo apt-get -f install  No errors on other command

---

