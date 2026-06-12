---
title: "Help with update-manager"
date: 2010-03-23
forum: General Help
---

### Post by deadcold94 on 2010-03-23
well every time i try to start synaptic i get 

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '76' is not known on line 1 in source list /etc/apt/sources.list, E:The list of sources could not be read.'  



it gets very annoying as i am very inexperienced with Linux i have not the slightest idea what this means or how to fix it?

---

### Post by patchwork on 2010-03-23
Can you post the output of ```
cat /etc/apt/sources.list
```

This is the file that specifies your repositories (and the file that is causing the error)

---

### Post by deadcold94 on 2010-03-23
76# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
# deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main # disabled on upgrade to jaunty
# deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main # disabled on upgrade to jaunty
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty /etc/apt/sources.list
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty /etc/apt/sources.list main/etc/apt/sources.list #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main/etc/apt/sources.list
deb [http://ppa.launchpad.net/jonabeck/ppa/ubuntu](http://ppa.launchpad.net/jonabeck/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/jonabeck/ppa/ubuntu](http://ppa.launchpad.net/jonabeck/ppa/ubuntu) jaunty main
mackenzie@I-*******-HATE-WINDOWS:~$

---

### Post by patchwork on 2010-03-23
Type ```
gksu gedit /etc/apt/sources.list
```Delete the 76 on the first line (It shouldn't be there), and save.  

Then ```
 sudo apt-get update
``` and try to re-open Synaptic


EDIT:  You'll also probably get an error about duplicate sources from your last two lines.  If you do, remove one of them in the same manner and run apt-get update again

---

### Post by deadcold94 on 2010-03-23
wow thank you so much!  something so simple. lol . i am very grateful. works perfectly.. although i do not understand how that could have been changed from what it is suppose to be

---

### Post by Trandre on 2010-03-23
I had a similar challange and solved it through these posts:

Locating the problem:
[http://ubuntuforums.org/showthread.php?t=1429144](http://ubuntuforums.org/showthread.php?t=1429144)

Resolved issues helped:
[http://ubuntuforums.org/showthread.php?t=1430660](http://ubuntuforums.org/showthread.php?t=1430660)
[http://ubuntuforums.org/showthread.php?t=1434436](http://ubuntuforums.org/showthread.php?t=1434436)


Trandre

---

