---
title: "Problems upgrading...broken packages??"
date: 2011-02-26
forum: General Help
---

### Post by listerdl on 2011-02-26
I am trying to perform an upgrade and received this error:

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Marking the upgrade (E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.)'This usually means that your installed packages have unmet dependencies"

I ran this line on terminal:

```

henry@ubuntu:~$ cat /var/log/dist-upgrade/apt.log | grep broken 
``` 
Package libc6 has broken Conflicts on libc6-i686
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
Package pm-utils has broken Conflicts on pm-utils-powersave-policy
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db-hpijs
Package libcdt4 has broken Conflicts on libgraphviz4
Package libept0 has broken Depends on libapt-pkg-libc6.10-6-4.8
Package libvlccore2 has broken Depends on vlc-data
Package libbrasero-media0 has broken Depends on brasero-common
Package libmagickcore2-extra has broken Depends on libgraphviz4
Package libvlc2 has broken Depends on libvlccore2
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
Package xserver-xorg has broken Depends on xserver-xorg-core
Package xserver-xorg-input-evdev has broken Depends on xorg-input-abi-11.0
Package xserver-xorg-video-rendition has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-s3virge has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-apm has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-ark has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-ati has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-tdfx has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-trident has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-fbdev has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-input-wacom has broken Depends on xorg-input-abi-11.0
Package xserver-xorg-video-mga has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-input-vmmouse has broken Depends on xorg-input-abi-11.0
Package xserver-xorg-input-mouse has broken Depends on xorg-input-abi-11.0
Package xserver-xorg-video-r128 has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-openchrome has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-vesa has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-siliconmotion has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-mach64 has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-sis has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-s3 has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-nv has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-savage has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-vmware has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-i128 has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-neomagic has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-chips has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-voodoo has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-i740 has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-input-synaptics has broken Depends on xorg-input-abi-11.0
Package xserver-xorg-video-sisusb has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-radeon has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-cirrus has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-intel has broken Depends on xorg-video-abi-8.0
Package xserver-xorg-video-v4l has broken Depends on xorg-video-abi-8.0
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0

So the above seems to be the problem, but when I go to synaptic and edit > fix broken packages, the message is then "Successfully fixed broken packages" but when I try to upgrade the cycle repeats itself.

Any ideas! THanks

---

### Post by listerdl on 2011-02-27
And if this helps this is my .list

```
henry@ubuntu:~$ gksudo gedit /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

Thanks again

---

