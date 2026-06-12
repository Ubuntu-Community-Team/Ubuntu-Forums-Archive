---
title: "can't open synaptic package manager"
date: 2010-11-21
forum: General Help
---

### Post by libioz on 2010-11-21
E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
 
**these are are errors i got when i try to open synaptic package manager!**
 
**this is the list:**
 
 
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

---

### Post by bananas4370 on 2010-11-21
> **libioz said:**
> E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
 
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

Remove the above lines and try again. Hopefully that resolves the issue. Those URL's don't exist with lucid as part of the path.

Cheers
Patrick

---

### Post by libioz on 2010-11-21
It worked!!!!!!!!
Thanks!!!!!!!!!

---

### Post by 3rdalbum on 2010-11-21
> **libioz said:**
> It worked!!!!!!!!
Thanks!!!!!!!!!

In future, don't modify the file directly - instead use the Repositories menu item from Synaptic to add repositories.

---

