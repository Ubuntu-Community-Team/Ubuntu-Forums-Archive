---
title: "Problem installing Eclipse IDE"
date: 2011-04-10
forum: General Help
---

### Post by ninnk on 2011-04-10
I've dual booted my Asus Laptop to run the new 11.04 Beta and Win7. -I'm new to Ubuntu. I am trying to download the Eclipse IDE with no success.. The error that I'm running into is:

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-6_1.4.2-1ubuntu2_amd64.deb 404  Not Found [IP: 91.189.92.171 80]
```Here is the output of my source list from running  ```
cat / etc/apt/sources.list
```:


```
#deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Beta amd64 (20110330)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

```
Just to make sure that the problem wasn't with security settings in my firewall, I shut down my firewall: ```
sudo ufw disable
``` and tried again. -It didn't help. Also, to make sure that the problem wasn't with my network permissions, I downloaded "Neverball" -A silly game from the Software Center and it worked just fine. 

I don't know if the version that is in the Software center is specifically build for Ubuntu or if I can just download it straight from the Eclipse web site. Any help is much appreciated.

Regards,
Ninn

---

### Post by vivek.pandey on 2011-04-10
is your system up to date?
try ```
 sudo apt-get update 
           sudo apt-get upgrade 
```

---

### Post by kiddfroster on 2011-04-10
Have you already tried downloading it through the software center? If that doesn't work, I would try downloading it again from the Eclipse website and try that. I have installed Eclipse from the Software center and everything worked for me.

---

### Post by vivek.pandey on 2011-04-10
> **kiddfroster said:**
> Have you already tried downloading it through the software center? If that doesn't work, I would try downloading it again from the Eclipse website and try that. I have installed Eclipse from the Software center and everything worked for me.

from the error message i guess OP is downloading it from software center or synaptic or using terminal but in either cases it is from ubuntu website and not from any other

---

### Post by ninnk on 2011-04-10
I am up to date, I just installed the newest beta version on Friday..

Also, I was trying to download from the software center - I will try Downloading from the Eclipse site first thing in the morning. Thanks for the advice guys, I will get back to you all asap.

-Ninn

---

### Post by lovinglinux on 2011-04-10
I use a version downloaded from Eclipse web site. Works like a charm.

---

