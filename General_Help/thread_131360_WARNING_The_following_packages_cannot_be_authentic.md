---
title: "WARNING: The following packages cannot be authenticated!"
date: 2006-02-16
forum: General Help
---

### Post by shams2 on 2006-02-16
hi,
I run the apt-get install kubuntu-desktop and this is the warning:
WARNING: The following packages cannot be authenticated!
  kdelibs-bin kdelibs-data kdelibs4c2 imagemagick libxine1c2 kamera
  kdegraphics-kfile-plugins kghostview koffice-libs koffice-data libkscan1
  kooka kpdf krita ksnapshot ksvg
can any one tell me what this mean please?

---

### Post by GeneralZod on 2006-02-16
That's odd.  Can you post your sources.list? Are you trying to install KDE 3.5.x?

Basically, it means that wherever you are getting the packages from has not actually signed the packages, which sounds pretty dodgy.  The warning might also occur if the packages are signed,  but you haven't whitelisted the signature.

---

### Post by shams2 on 2006-02-16
thanks for reply, this warning is with apt-get install kubuntu-desktop, this is my sources.list:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
## Uncomment the following two lines to fetch updated software from the network
 deb file:/store/ubuntu/ updates/
 deb [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy main restricted
#deb-src [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy universe
#deb-src [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by carlosqueso on 2006-02-16
It doesn't look like you're using any sketchy repos, so it may very well be okay to install those packages.   However, I would reccommend removing the pk before the address, as country-based mirrors tend to do silly things like have signature errors, or simply stop working from time to time

---

### Post by dcstar on 2006-02-16
[QUOTE=shams2]hi,
I run the apt-get install kubuntu-desktop and this is the warning:
WARNING: The following packages cannot be authenticated!
......[/QUOTE]
I had multiple repository errors today, but I did a full reload in Synaptic and everything fixed itself up.

I think the official repositories had been in the process of being updated with new package versions, so things got a little flaky for a while.

---

