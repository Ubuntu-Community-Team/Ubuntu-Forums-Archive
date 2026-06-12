---
title: "Skipped setting up Apt on karmic install"
date: 2009-10-29
forum: General Help
---

### Post by BrankoP on 2009-10-29
Hi all,

I have just installed 9.10 on my PC along side Vsta. I installed 64-bit version of 9.10, but during installation, install process stopped at one point, when it mentioned something about APT, and just stood there so i just press "skip" button that appeared...

Now, everything seems normal when booted, i can download software and updates etc... but when i was going to install Adobe Flash Plugin, there was error message saying something about flashplugin-install and dependencies...
I tried sudo apt-get install flashplugin-nonfree and also tried in pack manager, but there is constantly error messages about some dependencies...

Is this because of 64-bit incompatibility with flashplugin, or maybe something else?

Is there any way to reinstall Ubuntu or make a fresh install without interfering with grub dual boot?

Thanks in advance for help and sorry for long comment and probably bad English... :)

Regards!

---

### Post by Screwdriver0815 on 2009-10-29
> **BrankoP said:**
> Hi all,

I have just installed 9.10 on my PC along side Vsta. I installed 64-bit version of 9.10, but during installation, install process stopped at one point, when it mentioned something about APT, and just stood there so i just press "skip" button that appeared...

Now, everything seems normal when booted, i can download software and updates etc... but when i was going to install Adobe Flash Plugin, there was error message saying something about flashplugin-install and dependencies...
I tried sudo apt-get install flashplugin-nonfree and also tried in pack manager, but there is constantly error messages about some dependencies...

Is this because of 64-bit incompatibility with flashplugin, or maybe something else?

Is there any way to reinstall Ubuntu or make a fresh install without interfering with grub dual boot?

Thanks in advance for help and sorry for long comment and probably bad English... :)

Regards!
this error exists probably because you have skipped the APT-configuration. This is for setting up the software repositories and so on. Dependency errors occur mainly when the software sources are not set up properly.

You can re-install the system without affecting the dualboot. You just have to set it up right again in the installer. 

normally you also could fix this without re-installing but as Karmic has a different system for the software repositories I don't know what to do and would like to hand over to people who have experience with that

---

### Post by cariboo on 2009-10-29
Here is my /etc/apt/sources.list, it is pretty well bone stock.

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ -  amd64 (20090929.2)]/ karmic main restricted
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
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
```

Replace your /etc/apt/sources.list with mine, then run:

```
sudo apt-get update
```

Then you should be able to start installing packages.

---

