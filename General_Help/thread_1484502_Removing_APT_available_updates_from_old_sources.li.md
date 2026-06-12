---
title: "Removing APT available updates from old sources.list entry"
date: 2010-05-15
forum: General Help
---

### Post by eddiewould on 2010-05-15
Hey,

I'm running Ubuntu 10.04 on my laptop. I had the Ubuntu "Proposed Updates" in my /etc/apt/sources.list - I've taken it out because I've decided I don't want it.

However when I do an "apt-get upgrade" or "apt-get dist-upgrade" it's finding a whole bunch of "proposed" packages yet when it tries to install them I'm getting 404s - they're not on the mirror I'm using.

Question: Does anyone know how I can make apt/dpkg forget about these available updates from "proposed"?

So far I've tried "apt-get clean", "apt-get autoclean" and of course a "apt-get update". I've also tried a "apt-get install -f" 

Basically I want my system to go back to running only packages from repositories in my sources.list (I think some packages from "proposed" might have installed). 

My sources.list: 
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.ihug.co.nz/ubuntu/ lucid main restricted
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.ihug.co.nz/ubuntu/ lucid-updates main restricted
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.ihug.co.nz/ubuntu/ lucid universe
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid universe
deb http://mirror.ihug.co.nz/ubuntu/ lucid-updates universe
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.ihug.co.nz/ubuntu/ lucid multiverse
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid multiverse
deb http://mirror.ihug.co.nz/ubuntu/ lucid-updates multiverse
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nz.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://nz.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://mirror.ihug.co.nz/ubuntu/ lucid-security main restricted
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-security main restricted
deb http://mirror.ihug.co.nz/ubuntu/ lucid-security universe
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-security universe
deb http://mirror.ihug.co.nz/ubuntu/ lucid-security multiverse
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-security multiverse
deb http://mirror.ihug.co.nz/ubuntu/ lucid-backports restricted main multiverse universe

```

Any help is greatly appreciated

Eddie

---

### Post by eddiewould on 2010-05-15
One thing I should have pointed out, is that the packages it's trying to install from "proposed" are all packages I've currently got installed (and want to keep):

```
eddie@eddie-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
libgdata-common libgdata6 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa
libkpathsea5 liblircclient0 libnautilus-extension1 libsoup-gnome2.4-1
libsoup2.4-1 libtag1-vanilla libtag1c2a libvlc2 libvlccore2 mountall
nautilus nautilus-data nvidia-current-modaliases obexd-client pm-utils
python-cupshelpers python-ubuntuone-client rhythmbox
rhythmbox-plugin-cdrecorder rhythmbox-plugins software-center synaptic
system-config-printer-common system-config-printer-gnome
system-config-printer-udev tomboy totem totem-common totem-mozilla
totem-plugins transmission-common transmission-gtk ubuntuone-client
ubuntuone-client-gnome unattended-upgrades update-manager
update-manager-core vlc vlc-data vlc-nox vlc-plugin-pulse
46 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.0MB of archives.
After this operation, 487kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

---

### Post by eddiewould on 2010-05-19
Can no-one give me a hand with this? :(

---

### Post by ankspo71 on 2010-05-19
> My sources.list: 
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.ihug.co.nz/ubuntu/ lucid main restricted
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.ihug.co.nz/ubuntu/ lucid-updates main restricted
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.ihug.co.nz/ubuntu/ lucid universe
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid universe
deb http://mirror.ihug.co.nz/ubuntu/ lucid-updates universe
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.ihug.co.nz/ubuntu/ lucid multiverse
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid multiverse
deb http://mirror.ihug.co.nz/ubuntu/ lucid-updates multiverse
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="Red"]# deb http://nz.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://nz.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse[/COLOR]

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://mirror.ihug.co.nz/ubuntu/ lucid-security main restricted
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-security main restricted
deb http://mirror.ihug.co.nz/ubuntu/ lucid-security universe
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-security universe
deb http://mirror.ihug.co.nz/ubuntu/ lucid-security multiverse
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-security multiverse
[COLOR="Red"]deb http://mirror.ihug.co.nz/ubuntu/ lucid-backports restricted main multiverse universe[/COLOR]

```


Hi, I think you have disabled backports (in the middle), but still have backports enabled (in the last line). You can put a # in front of it to disable it.

---

