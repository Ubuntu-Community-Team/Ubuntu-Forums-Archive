---
title: "Problem with Sources list on upgrade to Karmic"
date: 2010-02-20
forum: General Help
---

### Post by sports fan Matt on 2010-02-20
I readded all my sources and ppa's on the upgrade but now they are disabled? Also I have a malformed line..Why would they be disabled if I changed them all one by one through software sources?

Error: Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 56 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

---

### Post by sports fan Matt on 2010-02-20
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/karmic-updates](http://archive.ubuntu.com/ubuntu/karmic-updates) main restricted
deb-src [http://archive.ubuntu.com/ubuntu/karmic-updates](http://archive.ubuntu.com/ubuntu/karmic-updates) restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/karmic](http://archive.ubuntu.com/ubuntu/karmic) universe
deb [http://archive.ubuntu.com/ubuntu/karmic-updates](http://archive.ubuntu.com/ubuntu/karmic-updates) universe
deb [http://archive.ubuntu.com/ubuntu/karmic](http://archive.ubuntu.com/ubuntu/karmic) multiverse
deb [http://archive.ubuntu.com/ubuntu/karmic-updates](http://archive.ubuntu.com/ubuntu/karmic-updates) multiverse
deb [http://us.archive.ubuntu.com/ubuntu/karmic-backports](http://us.archive.ubuntu.com/ubuntu/karmic-backports) main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/karmic-backports](http://us.archive.ubuntu.com/ubuntu/karmic-backports) main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/karmic-security](http://archive.ubuntu.com/ubuntu/karmic-security) main restricted
deb-src [http://archive.ubuntu.com/ubuntu/karmic-security](http://archive.ubuntu.com/ubuntu/karmic-security) restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/karmic-security](http://archive.ubuntu.com/ubuntu/karmic-security) universe
deb [http://archive.ubuntu.com/ubuntu/karmic-security](http://archive.ubuntu.com/ubuntu/karmic-security) multiverse
deb [http://downloads.sourceforge.net/pro...la/mozilla/apt](http://downloads.sourceforge.net/pro...la/mozilla/apt) all main
deb [http://archive.ubuntu.com/ubuntu/karmic-proposed](http://archive.ubuntu.com/ubuntu/karmic-proposed) restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/karmic-proposed](http://archive.ubuntu.com/ubuntu/karmic-proposed) restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/karmic-backports](http://archive.ubuntu.com/ubuntu/karmic-backports) restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/karmic-backports](http://archive.ubuntu.com/ubuntu/karmic-backports) restricted main multiverse universe

---

### Post by stoneage on 2010-02-20
I think line 56 should read 
deb [http://archive.ubuntu.com/ubuntu/dists/karmic](http://archive.ubuntu.com/ubuntu/dists/karmic) universe

The url [http://archive.ubuntu.com/ubuntu/karmic](http://archive.ubuntu.com/ubuntu/karmic) gives a 404

I think many of the others will be problematic too. Maybe you could try a different server?

---

### Post by sports fan Matt on 2010-02-20
I could, but I thought the main one was pretty solid.

---

### Post by stoneage on 2010-02-20
I would too. It seems odd that it has been moved. Did you add those manually?

---

### Post by sports fan Matt on 2010-02-20
I readded alot from ttp://ubuntuforums.org/showthread.php?p=5469046 manually cause thery had jaunty and now karmic versions.

---

### Post by sports fan Matt on 2010-02-20
I shouldnt have upgraded..Everything from a default install is installed and a broken package (ubuntu desktop) prevents me from uninstalling all the games and fluff..lol

Error is: E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory

---

### Post by sports fan Matt on 2010-02-20
I fixed the broken package..now it's a matter of cleaning up the packages installed :)

---

