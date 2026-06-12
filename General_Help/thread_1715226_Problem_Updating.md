---
title: "Problem Updating"
date: 2011-03-26
forum: General Help
---

### Post by siddhantchd on 2011-03-26
hey guys 
when i run the following command

> sudo apt-get update

i am getting this error 
> 
E: Some index files failed to download, they have been ignored, or old ones used instead.


what should i do

---

### Post by garvinrick4 on 2011-03-26
```
gedit /etc/apt/sources.list
```
Copy and paste this to a terminal
and post the results here.

---

### Post by siddhantchd on 2011-03-26
```
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick universe
deb http://in.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://in.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```

---

### Post by garvinrick4 on 2011-03-26
#Suggestions for your sources.list and cleaning up a bit.
1. In my signature you will see a main page click on it and choose maverick and install
medibuntu and it's key. Instructions in maverick manual under install repositorys.

2 .Go to this and take the # (comment sign) out of the front of partners repository: and maverick backports.
```
gksudo gedit /etc/apt/sources.list
```hit save and close:
```
sudo apt-get update
```Or go to Software Sources and check the box in other software I believe:
# After installing any repository must go to terminal and:
```
sudo apt-get update
```Now open a terminal:
```
sudo apt-get install libdvdcss2
```If you want to be capable of watching DVD's

open a terminal and:
```
sudo apt-get autoclean
``````
sudo dpkg --configure -a
``````
sudo apt-get -f install
``````
sudo apt-get update && sudo apt-get upgrade
```## This will get your medibuntu, Partners repositories and backports open,
libdvdcss2 installed,unneeded packages removed, check to fix broken packages and updated and upgraded. Let me know if any errors.

---

### Post by vivek.pandey on 2011-03-26
> **siddhantchd said:**
> hey guys 
when i run the following command



i am getting this error 


what should i do

sometimes that error pops up when you have a pretty slow net.... try updating again,,the error will go itself

---

### Post by siddhantchd on 2011-03-27
> **vivek.pandey said:**
> sometimes that error pops up when you have a pretty slow net.... try updating again,,the error will go itself

bro the net is working fine but still getting this error

---

### Post by vivek.pandey on 2011-03-27
> **siddhantchd said:**
> bro the net is working fine but still getting this error

did you try what garvinrick4 has asked to?

---

### Post by siddhantchd on 2011-03-27
> **vivek.pandey said:**
> did you try what garvinrick4 has asked to?

yea still getting that problem

---

### Post by Krytarik on 2011-03-27
Gee, this is again those India server! Try switching to another one via "System -> Software Sources", to "Main" if not any better.

Then update the package index:
```
sudo apt-get update
```If you are still getting connection errors, try another one.

Then run those commands to fix any broken dependencies, missing packages and upgrade:
```
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
sudo apt-get upgrade
```Greetings.

---

