---
title: "Apt-get duplicate sources issue"
date: 2009-07-29
forum: General Help
---

### Post by kogger on 2009-07-29
Whenever I run sudo apt-get update for the first time after having installed or uninstalled a package, I always get a list of errors regarding duplicate entries:

```
W: Duplicate sources.list entry http://us.archive.ubuntu.com jaunty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com jaunty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com jaunty/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com jaunty/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com jaunty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com jaunty-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

As it says at the bottom, running apt-get update again does seem to get rid of the error messages, but then the next time I need to update they're there again, so it's not really being corrected.

Here's my sources.list file:

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe
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
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
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

deb http://us.archive.ubuntu.com/ubuntu jaunty universe main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu jaunty universe main restricted universe

deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://ppa.launchpad.net/d.filoni/dillo/ubuntu jaunty main
deb-src http://ppa.launchpad.net/d.filoni/dillo/ubuntu jaunty main

deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
```

Any idea how to fix this?

---

### Post by ibutho on 2009-07-29
You need to edit /etc/apt/sources.list and comment out one of the duplicate entries for universe and partner repositories.

---

### Post by kogger on 2009-07-29
I swear I searched through there and couldn't find any duplicates. >_< Lol, well I guess that solves that.

---

### Post by Tapas Bose, India on 2009-09-25
[LIST]
[*]Open the terminal
[*]Login as root user
[/LIST]
> 
su


[LIST]
[*]And run
[/LIST]
> 
apt-get update


---

