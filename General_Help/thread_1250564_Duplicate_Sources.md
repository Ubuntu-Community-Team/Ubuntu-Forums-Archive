---
title: "Duplicate Sources"
date: 2009-08-26
forum: General Help
---

### Post by dazzler on 2009-08-26
Keep getting this error when checking for updates in synaptic

W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_openoffice-pkgs_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-mozilla-daily_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)

Heres my source list

Can someone tell me how to solve it, many thanks

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.



## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe restricted main
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

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
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main #openoffice
deb http://download.skype.com/linux/repos/debian stable non-free #skype
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main #firefox
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main #gnome-do
deb http://dl.google.com/linux/deb/ stable non-free #google
deb http://linux.getdropbox.com/ubuntu jaunty main #nautilus-dropbox
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main #ubuntu-tweak
deb http://wine.budgetdedicated.com/apt jaunty main #wine
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://apt.boxee.tv jaunty main
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
```

---

### Post by P4man on 2009-08-26
Well.. obviously "deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main" is in that list twice..

Not sure why it says the same for openoffice though. Unless Im blind, I only see it once.

---

### Post by dazzler on 2009-08-26
Cheers sorted it now, been bugging me for ages :)

I just removed the openoffice one anyway

---

