---
title: "Get error when adding sorcess"
date: 2010-01-15
forum: General Help
---

### Post by thelostubunt on 2010-01-15
Hi
I was trying to install some software (awn) when  whent to add it to my sources list it said this


Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

and then 


An error occurred

The following details are provided:
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/awn-testing-ppa-karmic.list
E: Unable to lock the list directory


and then

An error occurred

The following details are provided:
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/awn-testing-ppa-karmic.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


here is what i put in:

deb [http://ppa.launchpad.net/awn-testing/karmic](http://ppa.launchpad.net/awn-testing/karmic) koala main
deb-src [http://ppa.launchpad.net/awn-testing/karmic](http://ppa.launchpad.net/awn-testing/karmic) koala main


Here is my sources list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release  (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/awn-testing/karic](http://ppa.launchpad.net/awn-testing/karic) koala m
deb-src [http://ppa.launchpad.net/awn-testing/karmic](http://ppa.launchpad.net/awn-testing/karmic) koala main


I am trying to install Awn. I have gotten it to install in the preferances but not in applications. Also i need to install some fonts but i do not know how to can you help me. 

here is the font

bitstream vera sans Roman :popcorn:

---

### Post by arubislander on 2010-01-15
There seems to be a problem with the AWN ppa repositories. Why not install it from the main repositories?

---

### Post by slakkie on 2010-01-15
You are using KARMIC KOALA, is should be karmic

```

deb http://ppa.launchpad.net/awn-testing/karmic koala main
deb-src http://ppa.launchpad.net/awn-testing/karmic koala main

# Change to

deb http://ppa.launchpad.net/awn-testing/ karmic main
deb-src http://ppa.launchpad.net/awn-testing/ karmic main

```

---

### Post by thelostubunt on 2010-01-15
How do i install all respiratory? I am new to ubuntu.

---

### Post by thelostubunt on 2010-01-15
> **thelostubunt said:**
> How do i install all respiratory? I am new to ubuntu.
You said 

There seems to be a problem with the AWN ppa repositories. Why not install it from the main repositories?

How do i do it. i am new to ubuntu.

---

### Post by arubislander on 2010-01-15
Installing software from respository is not difficult. But first you need to delete de lines you added in your source.lst

Then you go to the Software Center, search for awn and click to select it and then choose install.

---

