---
title: "Update Manager HELP!"
date: 2010-01-31
forum: General Help
---

### Post by gmerindol on 2010-01-31
[IMG]http://i748.photobucket.com/albums/xx121/gmerindol/Screenshot.png[/IMG][IMG]http://s748.photobucket.com/albums/xx121/gmerindol/?action=view&current=Screenshot.png[/IMG]

This is what happens whenever I "Check for Updates" Using the Update Manager.

Code is exactly:

```

GPG error: http://ubuntu.compiz.net dapper Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

Failed to fetch http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz  404  Not Found

Some index files failed to download, they have been ignored, or old ones used instead.
```My Sources.list is

```
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net/ dapper main

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
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

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
```Thank you very much for your help.

---

### Post by plucky on 2010-01-31
```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of ```
deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net/ dapper main

```

Then ```
sudo apt-get update
``` from a termihnal or reload your sources.

Good Luck

---

### Post by gmerindol on 2010-01-31
> **plucky said:**
> ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of ```
deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net/ dapper main

```

Then ```
sudo apt-get update
``` from a termihnal or reload your sources.

Good Luck
Allright, but doesn't that mean it's gonna stop updating compiz and whatever the beerorkids is?

Thanks a lot tho.

---

### Post by stoneage on 2010-01-31
> **gmerindol said:**
> Allright, but doesn't that mean it's gonna stop updating compiz and whatever the beerorkids is?

Thanks a lot tho.

No, it will stop updating compiz from the Dapper repository which is nearly 4 years old now and probably no longer supported. You will still get updates for compiz for Karmic.

You might want to check your system to make sure you are not running any packages for Dapper, and if you find any purge them, then update and upgrade to bring things up to date.

If you want to stay bleeding edge for compiz there is probably a launchpad repository for Karmic you can enable instead of the dapper one.

Possibly this is it:-```

## Updates from the Compiz PPA: deb http://ppa.launchpad.net/compiz/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/compiz/ppa/ubuntu karmic main # Updates from the Compiz PPA: deb http://ppa.launchpad.net/compiz/ppa/ubuntu karmic main
```
> # Compiz-Fusion
# Improved usability with jazzed up graphics .. [http://www.compiz-fusion.org/](http://www.compiz-fusion.org/)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) karmic main
[http://guvnr.com/pc/karmic-repositories/](http://guvnr.com/pc/karmic-repositories/)

But don't take my word for it, check it out first.

---

