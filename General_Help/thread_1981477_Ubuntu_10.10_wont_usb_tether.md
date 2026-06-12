---
title: "Ubuntu 10.10 wont usb tether"
date: 2012-05-16
forum: General Help
---

### Post by waloshin on 2012-05-16
Ubuntu 10.10 wont usb tether with Samsung Galaxy Nexus, but the computer has no problem usb tethering with my Samsung Galaxy Rubgy.

---

### Post by wilee-nilee on 2012-05-16
Not necessarily related but, 10.10 is not supported it is end of life.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by waloshin on 2012-05-16
> **wilee-nilee said:**
> Not necessarily related but, 10.10 is not supported it is end of life.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

The ubuntu is ppc and wont upgrade to 11.04.

---

### Post by waloshin on 2012-05-16
Error during update


A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/natty/Release](http://ports.ubuntu.com/ubuntu-ports/dists/natty/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

[PHP]

cat /etc/apt/sources.list
deb http://ports.ubuntu.com/ubuntu-ports/ natty main restricted
# deb http://ports.ubuntu.com/ubuntu-ports/ maverick-updates main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ natty-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ maverick-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu maverick main
# deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://ports.ubuntu.com/ubuntu-ports/ natty-security main restricted multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ natty-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ natty-security universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ natty-security universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ natty-security multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ natty universe main restricted multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates universe main restricted multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ natty universe
deb http://ports.ubuntu.com/ubuntu-ports/ natty universe main
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates universe main
deb http://ports.ubuntu.com/ubuntu-ports/ natty-proposed universe main
 

[/PHP]

---

### Post by wilee-nilee on 2012-05-16
Read closer you have to change the source list I believe I have not done this myself. I don't think it is any different for a ppc with a quick look at your list.

Look for the required list. Be sure to be backed up first as well.

---

