---
title: "apt-get stuck"
date: 2011-10-18
forum: General Help
---

### Post by jayanthan on 2011-10-18
hi,

when i tried to use "apt-get update", it gets stuck at a certain stage.

it keeps on showing
> Get:n [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted amd64 Packages [8,261 B]
and the n goes on increasing

i tried changing sources, but it doesn't help.

i tried this - [http://ubuntuforums.org/showthread.php?t=878868](http://ubuntuforums.org/showthread.php?t=878868)
no change

i tried - [http://forum.doozan.com/read.php?2,4169](http://forum.doozan.com/read.php?2,4169)

then it shows
> Get:m [http://security.debian.org](http://security.debian.org) squeeze/updates/main i386 Packages [159 kB]
after every time n increases by nine steps, this shows up.

the connection doesn't have any problems so far.

---

### Post by CatKiller on 2011-10-18
You could just comment out that line for the time being so that you can get other updates and then uncomment it later if it's just a temporary problem.

---

### Post by jayanthan on 2011-10-18
sorry..
quoted :)

i removed restricted programs from the software sources.
now that i try to install vlc it cannot get data from main either.

---

### Post by CatKiller on 2011-10-18
It sounds like a more general connection problem then. I'm aware of the existence of threads where apt-get doesn't work even though a browser does, but I don't know what the solution is.

---

### Post by jayanthan on 2011-10-18
so can i use ftp repositories?
i dont quite use ftp that much. can u please give a hand?

---

### Post by ubu_dynamite on 2011-10-18
Using debian sources is not going to work when using ubuntu.

Can you post your /etc/apt/sources.list
```
cat /etc/apt/sources.list
```
Shouldbe something like this
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://nl.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

---

### Post by jayanthan on 2011-10-18
thanks, now its not needed anymore.
i changed all the repository protocols form http to ftp.
installation has never been so smooth.

---

