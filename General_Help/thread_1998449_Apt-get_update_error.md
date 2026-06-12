---
title: "Apt-get update error"
date: 2012-06-06
forum: General Help
---

### Post by aquascrotum on 2012-06-06
Hi all

Since upgrading, when I run an update I get an error along the lines of 

```
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

I've gone into my sources list and can't find any obvious duplications - output from /etc/apt/sources.list below.

Can anyone spot any duplications or why am I getting this problem?

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110927)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://gb.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multiverse universe
deb http://www.duinsoft.nl/pkg debs all
deb-src http://www.duinsoft.nl/pkg debs all
```

---

### Post by diesch on 2012-06-06
Quite likely the duplicate is in some file in  [I]/etc/apt/sources.list.d/  
[/I]

---

### Post by aquascrotum on 2012-06-06
OK, have looked here - contents are as follows.  Again, am not seeing any duplicates.  My upgrade crashed just before going for a restart when going to Precise from Oneiric in around the time when the upgrade cleanup was happening - might this problem be something to do with that?

```
google-chrome.list
google-chrome.list.save
happy-neko-ps3mediaserver-precise.list
happy-neko-ps3mediaserver-precise.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
oneiric-partner.list
oneiric-partner.list.distUpgrade
oneiric-partner.list.save
osmoma-audio-recorder-precise.list
osmoma-audio-recorder-precise.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_tiberiumalliances_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_tiberiumalliances_ubuntu.list.save
tualatrix-next-oneiric.list
tualatrix-next-oneiric.list.distUpgrade
tualatrix-next-oneiric.list.save
```

---

### Post by diesch on 2012-06-06
What's the output if you run
```
grep partner  /etc/apt/sources.list.d/* /etc/apt/sources.list
```
in a Terminal?

---

### Post by aquascrotum on 2012-06-06
As follows (thanks for the help)

```
/etc/apt/sources.list.d/oneiric-partner.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center
/etc/apt/sources.list.d/oneiric-partner.list.distUpgrade:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner #Added by software-center
/etc/apt/sources.list.d/oneiric-partner.list.save:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
```

---

### Post by diesch on 2012-06-06
> **aquascrotum said:**
> As follows (thanks for the help)

[CODE]/etc/apt/sources.list.d/oneiric-partner.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center


So here is the duplicate. I'd check if */etc/apt/sources.list.d/oneiric-partner.list *contains anything you need and remove the file otherwise.

---

