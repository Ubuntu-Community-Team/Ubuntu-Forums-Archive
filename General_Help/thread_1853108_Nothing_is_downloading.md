---
title: "Nothing is downloading"
date: 2011-10-01
forum: General Help
---

### Post by joesquire on 2011-10-01
Hello
I have searched the internet and tried many ways to solve this, but I can;t find a way to get it to work.
When I try to download anything from the software centre, it comes up with this:

Failed to download repository information
Check your Internet connection.
W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/Release](http://archive.ubuntu.com/ubuntu/dists/natty/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release](http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/Release](http://archive.ubuntu.com/ubuntu/dists/natty-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/natty-proposed/Release)  Unable to find expected entry 'independent/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Any help is appreciated
Thanks!

---

### Post by Krytarik on 2011-10-01
Please post the content of your "/etc/apt/sources.list" (use the #-button in the editor to enclose it in code-tags).

And, in anticipation of the result, you can use this site to create the proper default entries for your "sources.list":

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Greetings.

---

### Post by joesquire on 2011-10-02
Here is the sources.list

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu natty main restricted independent
deb-src http://archive.ubuntu.com/ubuntu natty main restricted independent

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted independent
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted independent

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://archive.ubuntu.com/ubuntu natty-security main restricted independent
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted independent
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb-src http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security multiverse
deb http://archive.ubuntu.com/ubuntu natty-proposed restricted main multiverse universe independent
```

I will also follow the link =)

---

### Post by joesquire on 2011-10-03
I offically broke Ubuntu, by doing something else haha never mind, so i had to reinstall it, which sorted the problem....i think. So thanks for your help!

---

