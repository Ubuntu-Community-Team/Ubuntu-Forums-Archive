---
title: "Trouble with Winetools"
date: 2006-01-30
forum: General Help
---

### Post by omegamike on 2006-01-30
I recently installed wine after months of living without any trace of windows, and I was hoping to also install winetools to go with it, but to my dismay it isn't showing up in the repositories even after adding the wine repositories on source forge. My question is if anyone has been able to install it recently and if so, how?

Here is the error message I receive when trying to install it:

bratticus@bratticus:~$ sudo apt-get install winetools
Reading package lists... Done
Building dependency tree... Done
Package winetools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package winetools has no installation candidate


Here is my apt-get sources list:

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

Any help would be appreciated!

---

### Post by o_fortuna on 2006-01-30
It seems like that repository doesn't include winetools anymore. You can always download it here:[WineTools]("http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz").
Once you've downloaded that to your desktop, extract it so you just have the uncompressed folder on your desktop. Now, do this in a terminal (Applications-->Accessories-->Terminal):
```
cd Desktop/winetools-0.9jo-III
sudo ./install
wt
```
That last command runs WineTools. From the website: **do not run as root**. That means don't use sudo with it. It will cause you a lot of pain. Trust me. I would know.

---

### Post by omegamike on 2006-01-31
Thanks a ton! Downloading that file and running those commands worked like a charm.

---

