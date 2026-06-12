---
title: "Can't apt-get update..."
date: 2010-04-29
forum: General Help
---

### Post by arrrghhh on 2010-04-29
So I added some PPA's for MPD, and now I can't apt-get update.  I commented out the new lines, and I STILL cannot apt-get update, seems to fail for the same reason... is there anything else I need to do to update my repo's?  Here's my sources.list and the errors:
```
# 
# deb cdrom:[Ubuntu-Server 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)]/ lucid main restricted

# deb cdrom:[Ubuntu-Server 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

#PS3 Media Server Repo
#deb http://deb.paissad.net/ unstable main contrib non-free
#deb-src http://deb.paissad.net/ unstable main contrib non-free
#deb http://ppa.launchpad.net/paissad/pms-linux/ubuntu lucid main
#deb-src http://ppa.launchpad.net/paissad/pms-linux/ubuntu lucid main

#libzen0 libmediainfo0 for above
# deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main

#MPD bleeding edge
# deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu lucid main

#More MPD Stuff
#deb http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu lucid main
#deb-src http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu lucid main
```
```
sudo apt-get update
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://ppa.launchpad.net/mpd-trunk/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release
Hit http://ppa.launchpad.net lucid Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Ign http://ppa.launchpad.net lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Hit http://security.ubuntu.com lucid-security/main Packages
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://archive.canonical.com lucid/partner Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://archive.canonical.com lucid/partner Sources
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
W: Failed to fetch http://ppa.launchpad.net/mpd-trunk/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Please help!!

---

### Post by plucky on 2010-04-29
> So I added some PPA's for MPD, and now I can't apt-get update. I commented out the new lines, and I STILL cannot apt-get update, seems to fail for the same reason... is there anything else I need to do to update my repo's?


From a terminal

```
ls -l /etc/apt/sources.list.d/
```

and see if there is a .list file in there that relates to the one that is giving you the error.

Good Luck

---

### Post by Seal Daemon on 2010-04-29
PPA doesn't contain anything related to mpd so there's obviously no way you could use it - remove the mpd-trunk entry and everything will be fine.

---

### Post by arrrghhh on 2010-04-29
> **plucky said:**
> From a terminal

```
ls -l /etc/apt/sources.list.d/
```

and see if there is a .list file in there that relates to the one that is giving you the error.

Good Luck

This was it, thanks.  I naively assumed that the sources.list file was the ONLY place this stuff went!

> PPA doesn't contain anything related to mpd so there's obviously no way you could use it - remove the mpd-trunk entry and everything will be fine.

I'm trying to get a newer version of MPD than 0.15.4, while still using a repo... any ideas?  There's a bug that segfaults MPD whenever it tries to play an AAC file, which evidently is patched in .6.  I'd like to go to .9, but NOT thru compiling it by hand, I want to be able to stay up-to-date.  Thanks!!

---

### Post by Seal Daemon on 2010-04-29
Believe me, *compiling by hand* will take less time and effort than trying to find a way to update it through PPA or something else of that kind.

---

### Post by arrrghhh on 2010-04-29
> **Seal Daemon said:**
> Believe me, *compiling by hand* will take less time and effort than trying to find a way to update it through PPA or something else of that kind.

A) last time I compiled MPD by hand, v0.15.9, it refused to "see" any of my music.  Tried mucking with permissions, nothing.  Plus, no init script.  
B) How do I keep it updated?
C) What if some packages in the repo's update past MPD and it breaks MPD?

Compiling from source just seems like the worst possible option, but I guess I can... I just don't want a big kludge of a system again that I'll need to blow away in a few years because it's so buggered up.

---

### Post by arrrghhh on 2010-04-29
I ended up getting it to work, after removing those files in /etc/apt/sources.list.d/ and uncommenting that last couple of lines of my sources.list got MPD up to date without compiling - and I get MPC and all the neccessaries along with it, MUCH better than compiling by hand.

If anyone is curious, [here's](http://ubuntuforums.org/showthread.php?t=1460338) a thread where I reveal the solution in-depth.  I have an entire conversation with myself as well, it's fun.

---

