---
title: "Broken Sources List"
date: 2012-07-06
forum: General Help
---

### Post by caffeinatedev on 2012-07-06
I seem to have broken my sources.list after adding ppa:ojno/unity-minimize-on-click

I tried removing the PPA via ppa-purge but the PPA doesn't show up in the sources.list. I printed my sources output via terminal
```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

## Spotify repository
deb http://repository.spotify.com stable non-free

```

I can neither open Ubuntu Software Center or Synaptic Package Manager. I can't update my sources.

Any help is appreciated.

---

### Post by wojox on 2012-07-06
Whats the error when you run:
```
sudo apt-get update
```

PPA's are usually stored in /etc/apt/sources.list.d/

---

### Post by Toz on 2012-07-06
> I tried removing the PPA via ppa-purge but the PPA doesn't show up in the sources.list.The entry would be placed in the /etc/sources.list.d directory in a file.

> I can neither open Ubuntu Software Center or Synaptic Package Manager. I can't update my sources.Are you getting an error message? What happens if you try a sources update from the command line? Open a terminal window, type in the following, and post back any errors you may get:
```
sudo apt-get update
```

---

### Post by caffeinatedev on 2012-07-07
> **wojox said:**
> Whats the error when you run:
```
sudo apt-get update
```

PPA's are usually stored in /etc/apt/sources.list.d/

My source list opens as /etc/apt/sources.list but the terminal output when I update my sources is /etc/apt/sources.list.d

I don't understand why that is, I'm still fairly new to Ubuntu/Linux.

---

### Post by caffeinatedev on 2012-07-07
> **Toz said:**
> The entry would be placed in the /etc/sources.list.d directory in a file.

Are you getting an error message? What happens if you try a sources update from the command line? Open a terminal window, type in the following, and post back any errors you may get:
```
sudo apt-get update
```

Output: ```
E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
E: The list of sources could not be read.

```

---

### Post by dino99 on 2012-07-07
to remove this ppa, into a terminal, run:

sudo rm /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list

---

### Post by Toz on 2012-07-07
> **caffeinatedev said:**
> My source list opens as /etc/apt/sources.list but the terminal output when I update my sources is /etc/apt/sources.list.d

I don't understand why that is, I'm still fairly new to Ubuntu/Linux.

When you add a PPA to your system, the information is put into a file in the /etc/apt/sources.list.d directory and not into /etc/sources.list directly. Follow dino99's suggestion to remove the affected entry.

---

### Post by caffeinatedev on 2012-07-07
> **dino99 said:**
> to remove this ppa, into a terminal, run:

sudo rm /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list

That worked thanks!

---

