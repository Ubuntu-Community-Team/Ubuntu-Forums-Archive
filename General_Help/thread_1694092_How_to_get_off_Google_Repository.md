---
title: "How to get off Google Repository"
date: 2011-02-23
forum: General Help
---

### Post by SyL on 2011-02-23
Hello Ubuntu-fellas,

I got in my apt update log the following hit to google repository,  eventhough there is no google repository within my sources.list file ...  and i do not have any google packages installed. 
I've been looking around a while and i'm now short of idea.




```
syl@mame:/opt$ sudo aptitude update 
*(...)*
**Get:1 http://dl.google.com stable Release.gpg [197B]                                             **
Hit http://ppa.launchpad.net karmic Release.gpg                          
Ign http://ppa.launchpad.net karmic/main Translation-en_IE               
Ign http://security.ubuntu.com karmic-security/universe Translation-en_IE
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_IE
Hit http://security.ubuntu.com karmic-security Release               
Hit http://ppa.launchpad.net karmic Release                          
Hit http://security.ubuntu.com karmic-security/main Packages        
**Ign http://dl.google.com stable/main Translation-en_IE**
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
**Get:2 http://dl.google.com stable Release [1,338B]**
Hit http://security.ubuntu.com karmic-security/multiverse Sources
**Get:3 http://dl.google.com stable/main Packages [471B]**
Fetched 2,006B in 2s (888B/s)
Reading package lists... Done

``````
 more /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main multiverse restricted universe
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://jp.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://jp.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://jp.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://jp.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://jp.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://jp.archive.ubuntu.com/ubuntu/ karmic universe
deb http://jp.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://jp.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://jp.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://jp.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://jp.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://jp.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

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
yeah, i stick to karmic for some reasons...


cheers !

---

### Post by snowpine on 2011-02-23
Check your /etc/apt/sources.list.d/ folder.

---

### Post by SyL on 2011-02-23
> **snowpine said:**
> Check your /etc/apt/sources.list.d/ folder.


That's it !!
Thanks a lot Dude :-D

There was a google-earth.list file in this directory

---

