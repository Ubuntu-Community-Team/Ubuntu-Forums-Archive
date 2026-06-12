---
title: "Can't install software with apt-get"
date: 2009-12-23
forum: General Help
---

### Post by Chunz0r on 2009-12-23
Hi, wonder if anyone can help,

Just installed karmic and I'm having a lot of trouble getting apt-get to work.

apt-get update gives the following errors:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release](http://archive.ubuntu.com/ubuntu/dists/karmic/Release)  Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


My sources.list:

> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

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
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse

Any ideas?

---

### Post by dcstar on 2009-12-24
> **Chunz0r said:**
> Hi, wonder if anyone can help,

Just installed karmic and I'm having a lot of trouble getting apt-get to work.

apt-get update gives the following errors:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release](http://archive.ubuntu.com/ubuntu/dists/karmic/Release)  Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

Those links work fine for me, you may well have network problems.

Select another repository and try again.

---

### Post by Soul-Sing on 2009-12-24
404 are server errors. Try it again after some time.

---

