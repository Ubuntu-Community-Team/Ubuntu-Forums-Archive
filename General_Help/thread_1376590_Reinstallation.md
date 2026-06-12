---
title: "Reinstallation"
date: 2010-01-09
forum: General Help
---

### Post by Lonnie82 on 2010-01-09
Hi,

I just installed ubuntu on my computer via partitioning. Now I have an errormessage that makes it impossible for me to get into the synaptic mannager and since I still havn\t installed to many of my own stuff I figured the easy fix would be to reinstall it over the same partition.

Problem is that I never partitioned a disk before and have no Idea how to do in the manual partitioning when I have deleted the excisting partition and have to add a new.

I really hope you can help me,

Lonnie

---

### Post by stoneage on 2010-01-09
Maybe a little off-topic, but what is the Synaptic error message? If that can be fixed maybe you don't need to reinstall?

---

### Post by Lonnie82 on 2010-01-09
When I start the package manager I get the following error:

E: Type 'wget' is not known on line 53 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Lonnie

---

### Post by stoneage on 2010-01-09
What does your /etc/apt/sources.list look like?

> sudo gedit /etc/apt/sources.list

---

### Post by Lonnie82 on 2010-01-09
Hi,

I'm completely new to linux - but this is what I get from the terminal (hope it's what you meant):

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

## Medibuntu - Ubuntu 8.04 "hardy"
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Lonnie

---

### Post by stoneage on 2010-01-09
Yes, that's exactly it.

It looks like the problem is the last line. If you remove that it should be back to normal.

I guess that last line should have gone into a Terminal instead. Possibly it also a mistake to use Hardy packages in Karmic, but I guess it depends which ones.

If you need the medibuntu repository it should look more like this:-
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
but you will also need to add the keyring.

Have a look here:-
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
it should explain it. 



I hope this helps.

---

### Post by Lonnie82 on 2010-01-09
Hi,

Thanks for the quick response - it worked like a charm...

Lonnie

---

