---
title: "tofrodos doesn't seem to install properly"
date: 2010-04-13
forum: General Help
---

### Post by pingtoft on 2010-04-13
I can't seem to install tofrodos on my Lucid box.
Both dos2unix and unix2dos is missing - I don't have the todos and fromdos folders in /usr/bin/ either.
I've tried the following but it doesn't work:
```
**sudo apt-get --purge autoremove tofrodos**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  tofrodos*
0 upgraded, 0 newly installed, 1 to remove and 98 not upgraded.
After this operation, 86,0kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 47414 files and directories currently installed.)
Removing tofrodos ...
Processing triggers for man-db ...

**sudo apt-get install tofrodos**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  tofrodos
0 upgraded, 1 newly installed, 0 to remove and 98 not upgraded.
Need to get 0B/20,4kB of archives.
After this operation, 86,0kB of additional disk space will be used.
Selecting previously deselected package tofrodos.
(Reading database ... 47405 files and directories currently installed.)
Unpacking tofrodos (from .../tofrodos_1.7.8.debian.1-2_i386.deb) ...
Processing triggers for man-db ...
Setting up tofrodos (1.7.8.debian.1-2) ...

```

My sources.list:
```
#
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://dk.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
#deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu intrepid main
#deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu intrepid main
deb http://ppa.launchpad.net/jcfp/ppa/ubuntu jaunty main
deb http://dk.archive.ubuntu.com/ubuntu lucid main universe
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu jaunty main

```

---

### Post by ughknight on 2010-05-12
I have not yet verified this, am about to try it now. But if you try to manually reinstall the deb, the info box says that the commands to invoke it have changed. It's now "fromdos" and "todos" instead of "dos2unix" and "unix2dos."

---

### Post by ughknight on 2010-05-12
I've tested the above, it works fine. Don't know why they changed the names; unix2dos and dos2unix are more descriptive in my book.

---

