---
title: "Deleted Repositories"
date: 2011-06-21
forum: General Help
---

### Post by Robbyx on 2011-06-21
Synaptic informed me that I had a number of duplicate entries. I removed them from the lists. Now I have the following error message:e


> Failed to fetch [http://ppa.launchpad.net//ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net//ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net//ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net//ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/user/ppa-nameppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/user/ppa-nameppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/user/ppa-nameppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/user/ppa-nameppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.


How do I bring them back? They are not in the dustbin.

---

### Post by inameiname on 2011-06-21
That error message occurs when a particular repo (a Launchpad PPA in your case) has no packages inside and/or is having issues. Sometimes the errors fix themselves, and when updated, your repos are fine; other times, they don't, and its best just to remove those repos. 

As such, there is nothing to bring back due to those errors, as the trouble isn't on your end. That said, I am unsure what you deleted.

---

### Post by Robbyx on 2011-06-21
I deleted the files that were in the lists directory that were said to be duplicates by synaptic. I could not find duplicates in the software sources.

---

### Post by gandaran on 2011-06-21
> **Robbyx said:**
> Synaptic informed me that I had a number of duplicate entries. I removed them from the lists. Now I have the following error message:e





How do I bring them back? They are not in the dustbin.
none of them work, (click the url links) they are probably incorrectly added to software sources, try removing them

---

### Post by Robbyx on 2011-06-21
Thank you for checking. I have now removed them from the other software tab in software sources, so that all I have in there relating to the operating system is:

Independent
Canonical partners (Source code)
Canonical Partners

In the ubuntu Software section of the sources I have the first four items ticked.

Should the above be sufficient to keep Ubuntu up to date?

---

### Post by inameiname on 2011-06-21
You only need the Official repos to keep it up-to-date. PPAs and other ones are just extras. I'll attach just that section of my sources.list to show you what I have:

```

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb http://us.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
deb-src http://extras.ubuntu.com/ubuntu natty main

```

---

### Post by Robbyx on 2011-06-22
Thank you. I am checking my existing sources.list, and because of the long and similar urls I find it muddling to accurately compare the two. Do you know of a utility that reports where the duplicates are and enables their removal in a more automated fashion?

---

### Post by dino99 on 2011-06-22
hey you only need to be awake and check the sources.list, not that hard :)

---

