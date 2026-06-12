---
title: "i add debian but it failed to fetch event update on ubuntu 12.04"
date: 2012-07-22
forum: General Help
---

### Post by marwa aly on 2012-07-22
i add debian on ubuntu 12.04 as: deb http: //dev.mikro.biologie.tu-muenchen.de/debian hardy non-free 


but it Failed to fetch event after update after i added in other software in ubuntu software center ..what can i do ????????????please help me 

Err [http://dev.mikro.biologie.tu-muenchen.de](http://dev.mikro.biologie.tu-muenchen.de) hardy/non-free Sources            
  404  Not Found 
W: Failed to fetch [http://dev.mikro.biologie.tu-muenchen.de/debian/dists/hardy/non-free/source/Sources](http://dev.mikro.biologie.tu-muenchen.de/debian/dists/hardy/non-free/source/Sources)  404  Not Found
 so what can i do???????????/////:confused::(
here is the gedit of source list:# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise universe
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://dev.mikro.biologie.tu-muenchen.de/debian](http://dev.mikro.biologie.tu-muenchen.de/debian) hardy non-free
deb-src [http://dev.mikro.biologie.tu-muenchen.de/debian](http://dev.mikro.biologie.tu-muenchen.de/debian) hardy non-free
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by PhantomTurtle on 2012-07-22
First of all you have added the repository for hardy, you need the one that says precise. Here is a link for the deb file for oneric - [http://dev.mikro.biologie.tu-muenchen.de/debian/dists/oneiric/non-free/binary-amd64/]("http://dev.mikro.biologie.tu-muenchen.de/debian/dists/oneiric/non-free/binary-amd64/"). Or you can just open your sources in gedit again and change it from hardy to precise. So, in your sources.list, at the end replace this ,
```
deb http://dev.mikro.biologie.tu-muenchen.de/debian hardy non-free
deb-src http://dev.mikro.biologie.tu-muenchen.de/debian hardy non-free
```
with this
```
deb http://dev.mikro.biologie.tu-muenchen.de/debian precise non-free
deb-src http://dev.mikro.biologie.tu-muenchen.de/debian precise non-free
```
(Second and third last line). Or you can download the deb file from that link and install.

---

