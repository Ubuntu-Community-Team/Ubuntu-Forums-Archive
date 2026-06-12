---
title: "adding QGIS repositories - what is this strange error?"
date: 2010-12-31
forum: General Help
---

### Post by BigBaka on 2010-12-31
Dear all,

As per [this webiste]("https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable") I added the "unstable" repositories for QGIS in 10.10 Maverick as follows

deb [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) maverick main 
deb-src [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) maverick main 

However, when I sudo apt-get update, at the end I get the following error.

W: Duplicate sources.list entry [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu/](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu/) maverick/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntugis_ubuntugis-unstable_ubuntu_dists_maverick_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Can someone please explain what this is, and if there is a way to fix it.

Thanks
BB

---

### Post by ajgreeny on 2010-12-31
Show us the output of the command ```
cat /etc/apt/sources.list 
```please and we should be able to tell you what to do.

---

### Post by BigBaka on 2010-12-31
Hi AJ

Here is the output

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://la.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://la.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse

##QGIS - unstable
deb http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu maverick main 
deb-src http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu maverick main 
```

The error is being generated from the last QGIS ppa's which is what I just put in there, but I'm not sure if there is something I can do to get rid of this message, or whether it is part and parcel of having these ppa's.

Cheers
BB

---

### Post by jvc26 on 2010-12-31
Just looking at [https://wiki.ubuntu.com/UbuntuGIS](https://wiki.ubuntu.com/UbuntuGIS) is this the thing you are trying to install? If so it makes sense to use their launchpad repos as they are tailored to ubuntu...?

J

---

### Post by BigBaka on 2010-12-31
Yes that is what I am using, albeit the "unstable" version, because the stable release is so delayed. I'm using the following launchpad site for info.

[https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable](https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable)

Not sure if there is something in there that I'm missing.

BB

---

### Post by ajgreeny on 2010-12-31
I think in that case you may have an **/etc/apt/sources.list.d** folder which contains the same line as your **/etc/apt/sources.list** in another plain text file.  Do a search there and you should be able to either comment out the line in one or the other file, or simply delete the line totally.  You will need to do this as root with ```
gksudo gedit /path/to/file
``` or just use the System ->Administration ->Software Sources from your menu.

---

### Post by BigBaka on 2010-12-31
Hi,

Thanks, that was it exactly. deleted the second ppa and all is now well.

Much appreciated
BB

---

