---
title: "Problem with the software sources."
date: 2009-08-01
forum: General Help
---

### Post by TopGear on 2009-08-01
Hello,

I am verry active in the dutch ubuntu forum, but now I have a verry weird problem.
I have a x64 Ubuntu 9.04 OS, but I use KDE.
First I had blocked updates, but that's solved with: "sudo apt-get dist upgrade".

Now I wanted to do something with my software sources, but I saw something that isn't right! See my sceenshot. Does anyone know what's wrong?

As you can see, have I still the sources from 8.04, and NOT 9.04?????

---

### Post by Soul-Sing on 2009-08-01
There are mixed software sources.
Could you please copy/paste your sources.list here?

---

### Post by TopGear on 2009-08-01
Here is mij sources.lst:

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
# deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock # uitgeschakeld op upgrade naar jaunty
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main

```

---

### Post by TopGear on 2009-08-22
Can you do something with it?

---

