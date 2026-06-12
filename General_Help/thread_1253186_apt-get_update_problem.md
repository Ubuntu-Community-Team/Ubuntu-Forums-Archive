---
title: "apt-get update problem"
date: 2009-08-29
forum: General Help
---

### Post by blur xc on 2009-08-29
When I run apt-get update I get this message:

```
Get:16 http://us.archive.ubuntu.com jaunty-proposed/universe Packages [8010B]
Fetched 445kB in 3s (111kB/s)   
Reading package lists... Done
W: Duplicate sources.list entry http://packages.medibuntu.org jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

Once I run it again, it completes successfully.

I'm confused because the medibuntu repos aren't in my sources.list twice (I did a text search in the file).  Here's my sources.list...```


# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

deb http://ppa.launchpad.net/compiz/ubuntu jaunty main
deb-src http://ppa.launchpad.net/compiz/ubuntu jaunty main

deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe

deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main

deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main

## Cinelerra
deb http://akirad.cinelerra.org akirad-jaunty main

deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
```

Thanks,
BM

---

### Post by oldos2er on 2009-08-29
Medibuntu usually is installed to /etc/apt/sources.list.d/medibuntu.list

---

### Post by blur xc on 2009-08-30
> **oldos2er said:**
> Medibuntu usually is installed to /etc/apt/sources.list.d/medibuntu.list


Why?  Can I just remove those lines from my /ect/apt/sources.list?  How many sources.list files are there?  And- How do I know which one to add a repository to?

Thanks,
BM

---

### Post by Liolikas on 2009-08-30
Basically error explains everything:
Duplicate sources.list entry

---

