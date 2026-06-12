---
title: "Firefox 8 update not in my repos yet?"
date: 2011-11-28
forum: General Help
---

### Post by winchendonsprings on 2011-11-28
I fear I am missing a main ppa.

The fact that I have not seen the update for Firefox 8, and the fact that a couple hundred of my packages are marked with (local or obsolete) makes me think I am missing a ppa.

Maybe someone can tell me what the repo Firefox 8 cam from?

Probably the same repo I am missing that holds Compiz, cups, deja-dup, empathy, gedit,  gnome-shell, gwibber etc....

---

### Post by ExileAmongYou on 2011-11-28
Could you post the output of ```
cat /etc/apt/sources.list
```?

---

### Post by winchendonsprings on 2011-11-28
Here it is. osuosl Is the Oregon State University Open Source Labs mirror, but I get the same results using the main server and the main US server

```
ry@ryan-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://ubuntu.osuosl.org/ubuntu/ oneiric main universe restricted multiverse
ry@ryan-laptop:~$ 


```

---

### Post by jocko on 2011-11-28
It looks like pretty much everything is missing from that file...
Here's mine (which works):
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu oneiric main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric universe
deb-src http://archive.ubuntu.com/ubuntu oneiric universe
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu oneiric multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb http://archive.ubuntu.com/ubuntu oneiric-security universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-security universe
deb http://archive.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://repository.spotify.com stable non-free
# deb-src http://repository.spotify.com stable non-free
deb http://download.virtualbox.org/virtualbox/debian oneiric contrib
# deb-src http://download.virtualbox.org/virtualbox/debian oneiric contrib

```

Edit: @wichendonsprins: you are missing the oneiric-backports, oneiric-security and oneiric-updates repos. You should be able to fix your file by adding these to the end:
```
deb http://ubuntu.osuosl.org/ubuntu/ oneiric-backports main universe restricted multiverse
deb http://ubuntu.osuosl.org/ubuntu/ oneiric-security main universe restricted multiverse
deb http://ubuntu.osuosl.org/ubuntu/ oneiric-updates main universe restricted multiverse
```

---

### Post by winchendonsprings on 2011-11-28
Thanks @jocko   How did this happen? This is a fresh install.

---

### Post by jocko on 2011-11-28
> **winchendonsprings said:**
> Thanks @jocko   How did this happen? This is a fresh install.
My guess is that it probably happened when you switched from the main repo to the osu mirror, but how and why it happened depends on how you did to switch (manual edit or using software-sources)...

---

### Post by crazy bird on 2011-11-28
Do you really want the latest (stable) Firefox on your system? Better to add this PPA: [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable),
 
And for Thunderbird this PPA:[https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable)

---

### Post by lovinglinux on 2011-11-28
> **crazy bird said:**
> Do you really want the latest (stable) Firefox on your system? Better to add this PPA: [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable),
 
And for Thunderbird this PPA:[https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable)

The *firefox-stable* ppa doesn't provide new versions of Firefox to Oneiric users, only to Maverick and Lucid, since on Oneiric the latest Firefox version is provided by the official repository.

See [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by digithal on 2011-11-28
> **crazy bird said:**
> Do you really want the latest (stable) Firefox on your system? Better to add this PPA: [https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable"),
 
And for Thunderbird this PPA:[https://launchpad.net/~mozillateam/+archive/thunderbird-stable]("https://launchpad.net/%7Emozillateam/+archive/thunderbird-stable")
There is no need to use the ppa for the moment, since firefox 8 is already in the official repositories and his sources.list is completed now :)

---

### Post by crazy bird on 2011-11-28
> **digithal said:**
> There is no need to use the ppa for the moment, since firefox 8 is already in the official repositories and his sources.list is completed now :)
 
Sweet :popcorn:

---

### Post by lovinglinux on 2011-11-28
> **digithal said:**
> There is no need to use the ppa for the moment, since firefox 8 is already in the official repositories and his sources.list is completed now :)

Actually, the *firefox-stable* ppa doesn't provide new versions of Firefox to Oneiric users, only to Maverick and Lucid, since on Oneiric the latest Firefox version is provided by the official repository.

See [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

