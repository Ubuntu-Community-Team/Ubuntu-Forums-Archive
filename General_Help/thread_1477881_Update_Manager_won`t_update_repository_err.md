---
title: "Update Manager won`t update repository err"
date: 2010-05-09
forum: General Help
---

### Post by ognyang on 2010-05-09
Hey folks,

For 3-4 days I`m unable to update my sistem. I don`t know why!
It says "could not download all repository indexes"
I tried to change the server but there is no difference.
Tried from the terminal - no success! 
You can see this in the [screenshot]("http://guglev.net/DATA/Screenshot.png")

EDIT:
Here`s a copy from my source.list
> 
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) lucid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) lucid main restricted multiverse
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) lucid universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) lucid-updates main restricted multiverse
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) lucid-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) lucid universe
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) lucid-security main restricted multiverse
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) lucid-security restricted main universe #Added by software-properties
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) lucid-security universe
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse


EDIT 2: In the "software sources" I unchecked the box with the "http://ppa.launchpad.net/madman2k/ubuntu" url and now everything is working fine. Do I need updates from this server? And is it possible the problem to be in their server?

EDIT 3: Is there some relation with the fprint?

---

