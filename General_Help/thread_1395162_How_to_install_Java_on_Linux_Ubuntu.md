---
title: "How to install Java on Linux Ubuntu"
date: 2010-01-31
forum: General Help
---

### Post by Petomatick on 2010-01-31
Hi how do i install java on linux?
I dont understand the ways they discribe it on internet and, when i try it in the "add or remove program" thingy, it says that there is an error and that i need to do something bla bla. And when i try to sudo apt-get install sun-java6-bin sun-java6-jre its says me to apt-get -f install but when i do that it asks me if im root even if im logged in as a root
also when i write sudo dpkg --configure -a it says Turning in java-common (0.28ubuntu3) ... (or something like that) and nothing more happends.
Here is my whole battle against the Error army:
```
[sudo] password for Nenad: 
E: dpkg was interrupted, you must manually run 'dpkg - configure-a' to correct the problem. 
Nenad Nenad @ ubuntu-desktop: ~ $ sudo dpkg - configure-a 
Sets the java-common (0.28ubuntu3) ... 

Nenad Nenad @ ubuntu-desktop: ~ $ lol 
bash: lol: command not found 
Nenad Nenad @ ubuntu-desktop: ~ $ sudo apt-get install sun-java6-bin sun-java6-jre 
Reading package lists ... Completed 
Building dependency tree 
Reading state information ... Completed 
You can possibly fix this by running "apt-get-f install ': 
The following packages have dependencies that can not be satisfied: 
  sun-java6-bin: Depends on: unixodbc but it will not be installed 
E: unmet dependencies. Try 'apt-get-f install "without packages (or specify a solution). 
Nenad Nenad @ ubuntu-desktop: ~ $ apt-get-f install 
E: Could not open lockfile / var / lib / dpkg / lock - open (13 Access Denied) 
E: Unable to lock the administration directory (/ var / lib / dpkg /), are you root? 
Nenad Nenad @ ubuntu-desktop: ~ $ su petomatick 
Password: 
petomatick Nenad @ ubuntu-desktop: / home / Nenad $ apt-get-f install 
E: Could not open lockfile / var / lib / dpkg / lock - open (13 Access Denied) 
E: Unable to lock the administration directory (/ var / lib / dpkg /), are you root? 
petomatick Nenad @ ubuntu-desktop: / home / Nenad $ sudo dpkg - configure-a 
[sudo] password for petomatick: 
petomatick is not in the sudoers file. This incident will be reported. 
petomatick Nenad @ ubuntu-desktop: / home / Nenad $
```its on swedish tho

---

### Post by philinux on 2010-01-31
Run this first.

```
sudo dpkg --configure -a
```

Not sure about the sudoers errors. Have you been a tickering. ;)

---

### Post by ajgreeny on 2010-01-31
OK, try first ```
sudo apt-get update
``` then the command shown in the above post ```
sudo dpkg --configure -a
```If you get an error message after trying the first, try the second one and then the first. Then try again the install commands ```
sudo apt-get install sun-java6-bin sun-java6-jre
```At one point in the terminal output you show
```
Nenad Nenad @ ubuntu-desktop: ~ $ apt-get-f install 
E: Could not open lockfile / var / lib / dpkg / lock - open (13 Access Denied) 
E: Unable to lock the administration directory (/ var / lib / dpkg /), are you root? 
Nenad Nenad @ ubuntu-desktop: ~ $ su petomatick 
Password: 
``` you tried the "su" command, for root, I presume.  That will not work in ubuntu; you need to use "sudo *command*" instead.  So you should have used ```
sudo apt-get -f install
```and forget about the su petomatick.

For more info on sudo and root permissions in ubuntu have a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

