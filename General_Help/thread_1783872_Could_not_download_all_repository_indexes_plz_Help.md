---
title: "Could not download all repository indexes plz Help"
date: 2011-06-16
forum: General Help
---

### Post by kazastyle on 2011-06-16
i do reload to synaptic package manager and its show:

[SIZE=3]**Could not download all repository indexes**[/SIZE]

**[SIZE=2]The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/SIZE]**

```
Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/natty/main/source/Sources  404  Not Found
Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.
``` And it have an icon up to bar left to language red with a white line! plz Help  me!

---

### Post by dagoss on 2011-06-16
Can you post your /etc/apt/sources.list please?

---

### Post by kazastyle on 2011-06-16
```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty restricted main #Added by software-properties
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ natty universe
deb http://gr.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
# security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
deb http://gr.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe #Added by software-properties
## developers who want to ship their latest software.
```

---

### Post by amauk on 2011-06-16
The PPA you've got for gdm2setup does not have any packages for Natty, seems to be only for Karmic & Lucid

Open up the software centre
Edit > Software sources
On the "other software" tab, untick the entries for gdm2setup

---

### Post by kazastyle on 2011-06-16
> **amauk said:**
> The PPA you've got for gdm2setup does not have any packages for Natty, seems to be only for Karmic & Lucid

Open up the software centre
Edit > Software sources
On the "other software" tab, untick the entries for gdm2setup


Where to put the code you write?

---

### Post by amauk on 2011-06-16
> **kazastyle said:**
> Where to put the code you write?what?

---

### Post by kazastyle on 2011-06-16
ok its done!!! thx very much !!

---

