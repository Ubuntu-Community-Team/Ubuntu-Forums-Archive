---
title: "synaptic package manager failed to fetch"
date: 2010-01-05
forum: General Help
---

### Post by spearfish on 2010-01-05
I can't reload the repositories in Synaptic Package Manager.  It says there is a problem with signature verification.

"The following signatures were invalid:  NODATA 1 NODATA 2"

Also, I can't seem to load any packages.  Always get the same error:

"W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/](http://us.archive.ubuntu.com/ubuntu/pool/main/)...
  Size mismatch"

It doesn't matter what I try to get.  Always a size mismatch.

All this because my wireless network keeps dropping out.  I think 9.10 should be called Buggy Badger. :(

---

### Post by spiderbatdad on 2010-01-05
Here's a copy of a default /etc/apt/sources.list
```
# deb cdrom:[Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```

---

### Post by spearfish on 2010-01-05
Thanks but I'm not really sure how that helps me.  I still get errors when I try to get stuff from the Synaptic Package Manager default servers.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/emacsen-common/emacsen-common_1.4.19ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/emacsen-common/emacsen-common_1.4.19ubuntu1_all.deb)
 Size mismatch

:confused:

What creates a size mismatch error?  Could this be a firewall issue?

---

### Post by spiderbatdad on 2010-01-05
I don't think a firewall issue. Something wrong with the package list download. Try
```
sudo apt-get clean
sudo apt-get update
```

---

