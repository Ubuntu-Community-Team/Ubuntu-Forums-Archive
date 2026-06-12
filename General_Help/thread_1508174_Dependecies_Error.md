---
title: "Dependecies Error"
date: 2010-06-12
forum: General Help
---

### Post by electrojustin on 2010-06-12
I've been trying to install vdkbuilder2, but it tries to install a bunch of unnecessary dependencies. Three or four of these dependencies fail and the package is not installed. Now, it seems that about half of my packages do this. They try to install the same long list of dependencies. The failed dependencies for vdkbuilder2 are as follows:  vdkbuilder2: Depends: libvdkbuilder2-dev but it is not going to be installed
               Depends: libvdk2-dev (>= 2.4.0-2) but it is not going to be installed
               Depends: libglib2.0-dev but it is not going to be installed
               Depends: libgtk2.0-dev but it is not going to be installed
I've tried updating and all repositories are enabled. Can anyone help?

---

### Post by zvacet on 2010-06-13
In applications>accessories>terminal type

```
sudo apt-get install libvdkbuilder2-dev
```

If you get any errors from this command.please post output here.But i you install this package try again to install vdkbuilder2.

---

### Post by _khAttAm_ on 2010-06-13
Which version of Ubuntu are you using?

try ```
sudo apt-get update
```
and then ```
sudo apt-get upgrade
```
and then try reinstalling the packages again.

---

### Post by electrojustin on 2010-06-13
I have already tried apt-get update and apt-get upgrade and that didn't work. Apt-get install libvdkbuilder2-dev gives me the following error message:  sudo apt-get install libvdkbuilder2-dev
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libvdkbuilder2-dev: Depends: libvdk2-dev (>= 2.0.3-3) but it is not going to be installed
                      Depends: libglib2.0-dev but it is not going to be installed
                      Depends: libgtk2.0-dev but it is not going to be installed
E: Broken packages
If i try to install the dependencies individually, they have the same long list of dependencies as the actual package and they fail to mark some of their dependencies. Same result as the package.

---

### Post by electrojustin on 2010-06-13
I'm using Lucid by the way.

---

### Post by mc4man on 2010-06-13
I would double check that all 4 ubuntu repo's are enabled and try using a different server - 
can all be done in System - Admin... - Software Sources

(all the packages mentioned here are in either main or universe and are certainly available

If continuing issue then post complete output of sudo apt-get update and possibly 
cat /etc/apt/sources.list

---

### Post by zvacet on 2010-06-13
Do what** mc4man** adviced to you.Under system>admin>software sources>check all under ubuntu software and first two under updates tab.After that run

```
sudo apt-get -f install
```

---

### Post by electrojustin on 2010-06-14
All repositories are enabled. Cat /etc/apt/sources.list is as follows: cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe #Added by software-properties
Sudo apt-get update, sudo apt-get upgrade, sudo apt-get install -f, sudo apt-get clean, and sudo apt-get autoclean do not give error messages, but they do not help. 
The main server gives me the same broken packages error message.

---

### Post by electrojustin on 2010-06-27
I have tried to install openssh-server, but it gives me the following error message: Depends: openssh-client (=1:5.3p1-3ubuntu3) but 1:5.3p1-3ubuntu4 is to be installed

---

### Post by electrojustin on 2010-06-28
I had an idea. What if the package dependencies that synaptic or aptitude are trying to install are outdated compared to the more recent version of the dependent package in the repositories? This seemed to occur with openssh-server at least, however I can't be sure about vdkbuilder2.

---

### Post by electrojustin on 2010-07-21
After more than 3 weeks  of this problem going unresolved, and other, more serious problems appearing, I have decided to reload my OS, however this time I'm going to load debian which I hear is a more stable distro. Thanks for the suggestions!
 
signing off...

---

### Post by electrojustin on 2010-07-21
Never mind debian dosn't support my wifi card. Installing ubuntu again.

---

### Post by roop_s on 2010-09-02
I'm running 10.04 x64 and had the same problem: couldn't install ssh server from tasksel, synaptic or aptitude. i received the same message.

the solution for me:

 sudo apt-get remove openssh-client
 sudo apt-get install openssh-server

the second command re-installs the client as well and then everything works.

---

### Post by derrickr on 2010-09-28
Good call roop_s!

I'm also running 10.04 but was getting dependency issues, stating:
 
The following packages have unmet dependencies.
  ssh: Depends: openssh-server but it is not going to be installed
E: Broken packages

This had me foxed, but luckily I found your solution :)

> **roop_s said:**
> 
 sudo apt-get remove openssh-client
 sudo apt-get install openssh-server


---

### Post by jpka on 2011-11-03
> **roop_s said:**
> 

 sudo apt-get remove openssh-client
 sudo apt-get install openssh-server



Thank you! it was very helpful in my special case when i can't update Ubuntu, due to i use special precompiled LTS version with RTAI kernel and other special hardware.
:KS
P.S. My error was exactly same
> **electrojustin said:**
> Depends: openssh-client (=1:5.3p1-3ubuntu3) but 1:5.3p1-3ubuntu4 is to be installed

---

