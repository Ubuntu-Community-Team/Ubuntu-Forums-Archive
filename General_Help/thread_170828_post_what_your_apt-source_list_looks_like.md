---
title: "post what your apt-source list looks like"
date: 2006-05-05
forum: General Help
---

### Post by k420 on 2006-05-05
i want to see what some other peoples  /etc/apt/sources.list looks like here is mine
```
deb http://download.skype.com/linux/repos/debian/ stable non-free 
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb ftp://ftp.nerim.net/debian-marillat/ sid main 
```

---

### Post by sYs^ on 2006-05-05
```
#
# deb cdrom:[Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20060310)]/ dapper main restricted

deb http://hu.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://hu.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://hu.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper universe

deb http://hu.archive.ubuntu.com/ubuntu/ dapper multiverse
deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://hu.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://security.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security multiverse

# deb ftp://ftp.nerim.net/debian-marillat sid main
# deb ftp://ftp.nerim.net/debian-marillat etch main

# deb http://www.beerorkid.com/compiz/ dapper main

deb http://wine.sourceforge.net/apt/ binary/

# deb http://xgl.compiz.info/ dapper main
```

But there's a lots of threads like this on this forum. :>

---

