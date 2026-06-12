---
title: "cupsys error on 10.10 server"
date: 2011-03-14
forum: General Help
---

### Post by abandonedthe_mulletator on 2011-03-14
I'm trying to set up a cups print server on 10.10 server.  When I run
```
sudo apt-get install cupsys
```
i get this error
```
E: Unable to locate package cupsys
```

I can find and install all kinds of other stuff and this is a fresh install.

Here's my /etc/apt/sources.list
```
#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick universe
deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu maverick main
# deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

```

Any ideas?

---

### Post by abandonedthe_mulletator on 2011-03-16
Please help, I need to set up this print server right away.

---

### Post by dragonfly41 on 2011-03-16
[SIZE=2]I had problems getting my printer to work LaserJet 2100M and here is what I found ..

[http://ubuntuforums.org/showthread.php?t=1707500](http://ubuntuforums.org/showthread.php?t=1707500)

At first CUPS server could not be connected then I found the forum thread.[/SIZE]

---

### Post by abandonedthe_mulletator on 2011-03-16
Thanks for the response.  That is a totally different problem though.  This seems to be an** apt problem** and not related to setting up the cups server.  I probably put the wrong title for the thread.

---

### Post by abandonedthe_mulletator on 2011-03-16
Can someone please help me?

Here is my kernel if that helps,
```
uwg@plotter:~$ uname -r
2.6.35-22-generic-pae
```

---

### Post by abandonedthe_mulletator on 2011-03-16
I searched for the cupsys package using my old server running 8.10.

This is what it shows,
```
~$ sudo apt-cache search cupsys
cupsys - Common UNIX Printing System (transitional package)

```

What is a transitional package?

On the new server running 10.10 I get this,
```
uwg@plotter:~$ sudo apt-cache search cupsys
cupsys-driver-gutenprint - Transitional package
libcups2 - Common UNIX Printing System(tm) - Core library
libcups2-dev - Common UNIX Printing System(tm) - Development files CUPS library

```

---

