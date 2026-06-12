---
title: "Trying to get rid of Firefox 4 beta NAMOwhatever and revert to current stable version"
date: 2011-01-27
forum: General Help
---

### Post by tk189 on 2011-01-27
The other day during an update I ended up stuck with the new Firefox 4 beta codename Namosomethingorother that i actually didn't want.

I didn't notice any request anyway to install the damn thing. At whatever point it appeared i lost my install of 3.6.13 and have been trying to get rid of 4beta (i'm not interested in testing the bloody thing, I want to get some work done using the stable vers)

I've tried uninstalling it, purging it and god knows what else but I am really struggling to just re-install 3.6.13

i keep getting an error in terminal that refers to firefox 4 even though it appears not to exist finally...

I am a newbie but I like to look for answers first rather than blindly ask questions but:

How do I just install firefox 3.6.13? either from unpacking a download or doing it via sudo magic?

tried this:

```
sudo apt-get purge firefox-4.0

sudo apt-get update

sudo apt-get install --reinstall firefox
```

and the damn firefox 4 beta Namowhatsit is re-installed....

DO NOT WANT!!!

---

### Post by hhh on 2011-01-27
Post the contents of /etc/apt/sources.list here.

---

### Post by Vaphell on 2011-01-27
shouldn't 4.0 be called minefield?
if you got that firefox from ppa (i suspect mozilla-daily) - uninstall firefoxes, go to software sources, disable the ppa, install firefox again from official repos.

---

### Post by hhh on 2011-01-27
@Vaphell, Minefield is the name of the Firefox nightly builds, but Firefox 4 is up to beta 9 and all the betas and release candidates are branded as Firefox.

---

### Post by tk189 on 2011-01-27
> **hhh said:**
> Post the contents of /etc/apt/sources.list here.

Please see below.

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://fr.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ maverick universe
deb http://fr.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fr.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

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
```


Whatever the fix i hope it appears soon, the beta is buggy as hell today (it's not been too bad until now) but I'm trying to access Google web fonts directory for something I'm working on and as soon as the page finishes loading, Namakakka crashes.

---

### Post by hhh on 2011-01-27
I'm in a bit of a rush, but the quick fix is to go here...
[http://packages.ubuntu.com/maverick/firefox](http://packages.ubuntu.com/maverick/firefox)
...scroll to the bottom and pick your architecture (amd64 if you have a 64 bit processor, i386 if not) and download Firefox 3.6 (right click the mirror and choose "Save link as...", then purge your existing Firefox and install 3.6 with Gdebi. Of course, until we figure what's pulling Firefox 4 your system will prompt you for an update, don't run it (or put a hold on 3.6 using Synaptic Package Manager).

That archive you are using has Firefox 4 in it, I'm not sure why (and I'm not on Maverick to test)...
[http://fr.archive.ubuntu.com/ubuntu/pool/main/f/firefox/](http://fr.archive.ubuntu.com/ubuntu/pool/main/f/firefox/)

Can someone on Maverick chime in here please?

---

### Post by tk189 on 2011-01-28
> **hhh said:**
> I'm in a bit of a rush, but the quick fix is to go here...
[http://packages.ubuntu.com/maverick/firefox](http://packages.ubuntu.com/maverick/firefox)
...scroll to the bottom and pick your architecture (amd64 if you have a 64 bit processor, i386 if not) and download Firefox 3.6 (right click the mirror and choose "Save link as...", then purge your existing Firefox and install 3.6 with Gdebi. Of course, until we figure what's pulling Firefox 4 your system will prompt you for an update, don't run it (or put a hold on 3.6 using Synaptic Package Manager).

That archive you are using has Firefox 4 in it, I'm not sure why (and I'm not on Maverick to test)...
[http://fr.archive.ubuntu.com/ubuntu/pool/main/f/firefox/](http://fr.archive.ubuntu.com/ubuntu/pool/main/f/firefox/)

Can someone on Maverick chime in here please?

Cheers for your help, much appreciated. Had a bit of a nightmare day today but I'll give that a go tomorrow. Thanks again.

---

