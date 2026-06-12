---
title: "repo Help"
date: 2010-10-20
forum: General Help
---

### Post by yusuo85 on 2010-10-20
could someone please help me by posting all your repo for ubuntu mine keeps coming up malformed and im having trouble getting it back to standard install ones, can someone help me by posting their sources.lst

---

### Post by plucky on 2010-10-20
> **yusuo85 said:**
> could someone please help me by posting all your repo for ubuntu mine keeps coming up malformed and im having trouble getting it back to standard install ones, can someone help me by posting their sources.lst

It would help if you posted what version you have installed.

Or Go [Here](http://repogen.simplylinux.ch/)

Good Luck

---

### Post by yusuo85 on 2010-10-20
i tried the link you gave me and thats what messed up my repo, I have maverick installed, I was wondering if i could have the default repos for maverick, the ones you get with a fresh install but was hoping someone would copy/poaste them here for me

---

### Post by bodhi.zazen on 2010-10-20
> **yusuo85 said:**
> i tried the link you gave me and thats what messed up my repo, I have maverick installed, I was wondering if i could have the default repos for maverick, the ones you get with a fresh install but was hoping someone would copy/poaste them here for me

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Or you can use these two lines:

```
deb http://us.archive.ubuntu.com/ubuntu/ maverick main universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-security main universe multiverse
```

---

### Post by plucky on 2010-10-20
> i tried the link you gave me and thats what messed up my repo, I have maverick installed, I was wondering if i could have the default repos for maverick, the ones you get with a fresh install but was hoping someone would copy/poaste them here for me 

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Alpha amd64 (20100803.1)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

```


Good Luck

---

