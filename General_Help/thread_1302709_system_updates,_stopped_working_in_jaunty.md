---
title: "system updates, stopped working in jaunty"
date: 2009-10-27
forum: General Help
---

### Post by dj-toonz on 2009-10-27
Hi all, For the past week now I've not been able to get any system updates, when I do a sudo apt-get update & then a sudo apt-get dist-upgrade this is what I get

toonz@toonz-laptop:~$ sudo apt-get dist-upgrade
[sudo] password for toonz: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
toonz@toonz-laptop:~$ 


here's the result for my etc/apt/sources.list

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner #Jaunty Partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

It work's on the desktop but not the laptop, I normally get daily updates for songbird, Firefox & others but haven't been getting anything (all my ppa's are in etc/apt/sources.d)

---

### Post by dcstar on 2009-10-27
> **dj-toonz said:**
> Hi all, For the past week now I've not been able to get any system updates, when I do a sudo apt-get update & then a sudo apt-get dist-upgrade this is what I get

toonz@toonz-laptop:~$ sudo apt-get dist-upgrade
[sudo] password for toonz: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
toonz@toonz-laptop:~$ 
.........

Why do you think that a Distribution Upgrade from a current system (which there is no upgrade for) is going to do anything?

---

### Post by dj-toonz on 2009-10-27
When I've done just a normal update in the past it's come back with i.e 5 keeped back, that's why I've always done a dist-upgrade to fully update the system & not keep any files back as I've got the mozilla daily ppa repos & a few other daily ppa repos, but like I've said, none have been working for the past week, even when I do just a sudo ap-get update & a sudo apt-get upgrade, I still get 0 for everything :-(

---

