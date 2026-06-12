---
title: "My software source list has just gone"
date: 2012-03-24
forum: General Help
---

### Post by Spyderkid on 2012-03-24
After the / drive got corrupt a few days ago when I had to fix it using fsck. My software source list has seemed to have disapeared.

I can't open the update manager, and whenever I log in I get an error message saying that something is wrong with the software sources.

Anyone know where I can find the default source list for the UK?

---

### Post by jerome1232 on 2012-03-24
First check your lost+found folder (only root can open it, and it's found at the root of your partition, so /lost+found)

It's possible, although unlikely, that it is there intact and just needs to be moved.


That being said there is a nifty site for reconstructing your sources.list file

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Cheesemill on 2012-03-24
> **Spyderkid said:**
> Anyone know where I can find the default source list for the UK?
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by davidvandoren on 2012-03-24
can't you just boot into live cd then go to etc/apt and use that sources list?

or sudo gedit /etc/apt/sources.list
and copy and paste. Save and close 
then open system administration Software sources.

and choose what you want.
   this is for ubuntu 10.04
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://tw.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://tw.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse
```

---

