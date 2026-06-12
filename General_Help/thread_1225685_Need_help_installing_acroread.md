---
title: "Need help installing acroread"
date: 2009-07-28
forum: General Help
---

### Post by Buce on 2009-07-28
Acroread doesn't seem to install for me. I'm pretty sure I added the medibuntu repo correctly, but no dice.

```
woody@bender:~$ sudo apt-get install acroread
[sudo] password for woody: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate
```

Here are my two .list files:

```
woody@bender:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://packages.medibuntu.org/ hardy free non-free
```

```
woody@bender:~$ cat /etc/apt/sources.list.d/medibuntu.list 
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free #Medibuntu - Ubuntu 8.04 LTS "hardy heron"
#deb-src http://packages.medibuntu.org/ hardy free non-free #Medibuntu (source) - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free #Medibuntu - Ubuntu 8.04 LTS "hardy heron"
#deb-src http://packages.medibuntu.org/ hardy free non-free #Medibuntu (source) - Ubuntu 8.04 LTS "hardy heron"
```

---

### Post by credobyte on 2009-07-28
Isn't acroread available only for x64 platforms ?

---

### Post by Buce on 2009-07-29
Oh, I didn't realize that. I know I had acroread working on Arch...although, looking closer, it seems that was a PKGBUILD.

---

### Post by Buce on 2009-07-31
Hm. Looks like acroread is available from the canonical repo. To get it, I uncommented this in my /etc/apt/sources.list:

```
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
```

And I think that was it...I don't remember there being a pgp key or anything. I've added a few other repos in the past few days, though, so in case that wasn't the one, here's the other repos I've got:

```
woody@bender:~$ cat /etc/apt/sources.list.d/*
# Open Office 3.x
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main

# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
deb-src http://ppa.launchpad.net/psyke83/ubuntu hardy main

# Deluge BitTorrent Client
deb http://ppa.launchpad.net/deluge-team/ubuntu hardy main universe
deb-src http://ppa.launchpad.net/deluge-team/ubuntu hardy main universe
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free #Medibuntu - Ubuntu 8.04 LTS "hardy heron"
deb-src http://packages.medibuntu.org/ hardy free non-free #Medibuntu (source) - Ubuntu 8.04 LTS "hardy heron"
```

---

