---
title: "Help..."
date: 2010-03-19
forum: General Help
---

### Post by maubulak on 2010-03-19
Ciao,
I'm new to ubuntu 9.10. Actually I got problem with synaptic package manager. I can't open it. Everytime i get this message..

An error occured
The following details are provided
E: line 49 in  /etc/apt/sources.list file is incorrect (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Can help me? Thanks...

---

### Post by n0dix on 2010-03-19
Post your /etc/apt/sources.list file.

---

### Post by maubulak on 2010-03-19
here it is

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic main multiverse restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-updates universe

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
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-security main multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-security universe main #Added by software-properties
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-backports main universe restricted multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-backports main universe restricted #Added by software-properties
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-proposed universe main restricted multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-proposed universe main restricted #Added by software-properties
deb [http://archive.ubuntu.com//ubuntu/karmic](http://archive.ubuntu.com//ubuntu/karmic) main.
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security universe main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-security main restricted #Added by software-properties
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

Thanks..!!!

---

### Post by n0dix on 2010-03-19
In this line:
```
deb http://archive.ubuntu.com//ubuntu/karmic main.
```
Without dot.

---

### Post by Iowan on 2010-03-19
Same line (4th from last) - double slashes?```
deb http://archive.ubuntu.com[COLOR="Red"]//[/COLOR]ubuntu/karmic main.
```

---

### Post by maubulak on 2010-03-20
Thanks a lot. The problem is just risolved!!!!

---

### Post by cottfcfan on 2010-03-20
Wrong thread!!

---

### Post by 3rdalbum on 2010-03-20
> **maubulak said:**
> Thanks a lot. The problem is just risolved!!!!

In future it would be a good idea to use the System > Administration > Software Sources program to add new lines to your sources.list; it won't let you add any incorrect lines.

---

### Post by Iowan on 2010-03-20
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :D

---

