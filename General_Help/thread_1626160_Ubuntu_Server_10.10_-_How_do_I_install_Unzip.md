---
title: "Ubuntu Server 10.10 - How do I install Unzip?"
date: 2010-11-19
forum: General Help
---

### Post by anthony62490 on 2010-11-19
I am trying to set up a dedicated gaming server, but I can't seem to get the unzip software to install (hopefully not an omen).

```
sudo apt-get install unzip
E: Package 'unzip' has no installation candidate
```

I have scoured Google for an answer to this, but nothing seems to work.

Did something change between 9.10 and 10.10? Or are things done very differently between the Server and Desktop versions of Ubuntu?

---

### Post by asmoore82 on 2010-11-19
Have you ```
sudo apt-get update
``` since you installed?

I would have thought `unzip` would be included in all *buntu variants out-of-the-box.

---

### Post by endotherm on 2010-11-19
not sure what repositories are included in the server edition, but my guess is you don;t have some of the more "restricted" ones. 
what is the output of 
```
cat /etc/apt/sources.list
```

here is mine:
```
orenji:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

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

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://ppa.launchpad.net/ubuntu-desktop/gnome3-builds/ubuntu maverick main
deb-src http://ppa.launchpad.net/ubuntu-desktop/gnome3-builds/ubuntu maverick main
deb http://ppa.launchpad.net/cimi/theming/ubuntu maverick main
deb-src http://ppa.launchpad.net/cimi/theming/ubuntu maverick main
```

---

### Post by CharlesA on 2010-11-19
Hrm. I was able to install that program on 10.04 and 10.10.

What does this return:

```
apt-cache search unzip
```

The repos are the same between server and desktop versions as far as I know.

---

### Post by anthony62490 on 2010-11-19
*headdesk* That was unusually straightforward. Thanks.

---

