---
title: "Why do I need Edubuntu disc every time I update?"
date: 2010-11-23
forum: General Help
---

### Post by BuddyThirteen on 2010-11-23
Every time I update anything, I'm asked to insert my Edubuntu disc. I booted from the CD once and ran it in LiveCD mode. I'm pretty sure I've never installed anything from it. So why do I need to put it in all the time? I'm not even running Edubuntu. I looked at the software sources, and the only CD listed is the Ubuntu one, and it's unchecked anyway, so how do I make it stop wanting the Edubuntu CD? Halp, please.

---

### Post by plucky on 2010-11-23
> **BuddyThirteen said:**
> Every time I update anything, I'm asked to insert my Edubuntu disc. I booted from the CD once and ran it in LiveCD mode. I'm pretty sure I've never installed anything from it. So why do I need to put it in all the time? I'm not even running Edubuntu. I looked at the software sources, and the only CD listed is the Ubuntu one, and it's unchecked anyway, so how do I make it stop wanting the Edubuntu CD? Halp, please.

Open a terminal and ```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
``` and post the output to the forum.


Good Luck

---

### Post by BuddyThirteen on 2010-11-23
It's a bit verbose, but here you go:

```
camaron@ubuntu-lvnrm:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb cdrom:[Edubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main multiverse restricted universe
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

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
deb-src http://security.ubuntu.com/ubuntu maverick-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse

camaron@ubuntu-lvnrm:~$ ls -l /etc/apt/sources.list.d/
total 12
-rw-r--r-- 1 root root 130 2010-11-22 23:49 kilian-f_lux-maverick.list
-rw-r--r-- 1 root root 130 2010-11-22 23:49 kilian-f_lux-maverick.list.save
-rw-r--r-- 1 root root 134 2010-11-22 23:49 tiheum-equinox-maverick.list
camaron@ubuntu-lvnrm:~$ 

```
I see the Edubuntu up there... how do I get rid of it?

---

### Post by Grenage on 2010-11-23
> **BuddyThirteen said:**
> I see the Edubuntu up there... how do I get rid of it?

I think edubuntu has gedit:
```
gksu gedit /etc/apt/sources.list
```

Comment out the source, so the CDROM lines look like:

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# deb cdrom:[Edubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main multiverse restricted universe

```

**OR**

Go to *Administration/Update Manager*.
Click on *settings*.
Untick the CDROM as a source.

---

### Post by BuddyThirteen on 2010-11-23
> **Grenage said:**
> Go to *Administration/Update Manager*.
Click on *settings*.
Untick the CDROM as a source.
That's the part that wasn't working. It only showed the Ubuntu disc, and the box was already cleared.

However...
> I think edubuntu has gedit:
```
gksu gedit /etc/apt/sources.list
```Comment out the source, so the CDROM lines look like:

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# deb cdrom:[Edubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main multiverse restricted universe

```****
This seems to have worked. The Ubuntu one was already commented, probably because I had that box cleared. So I commented the edubuntu one, and I'm about to test and see if it worked.

...

Yep! Didn't ask for my CD. Thank you for the help :-D

---

