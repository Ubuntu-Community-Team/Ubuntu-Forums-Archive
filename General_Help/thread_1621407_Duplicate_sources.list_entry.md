---
title: "Duplicate sources.list entry"
date: 2010-11-14
forum: General Help
---

### Post by Robbyx on 2010-11-14
This error comes from the update manager, but I can not see  duplicate entries in the software sources. Is there a program that removes duplicate sources? If not how do I find the duplicate entries. 

> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)

Robin

---

### Post by gandaran on 2010-11-14
type in terminal
```
sudo gedit /etc/apt/sources.list 
```
post the output if you need help

---

### Post by coffeecat on 2010-11-14
You can edit sources.list yourself with:

```
gksudo gedit /etc/apt/sources.list
```If you're unsure of which line to remove, post the contents of /etc/apt/sources.list and someone will help.

---

### Post by Robbyx on 2010-11-14
I can't see the duplicate.

This is the error message again:

> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partne r_binary-i386_Packages) 


```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse universe main restricted


## handwriting font
deb http://ppa.launchpad.net/andrewsomething/ubuntu maverick main
deb-src http://ppa.launchpad.net/andrewsomething/ubuntu maverick main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse universe main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security multiverse universe main restricted
deb http://packages.medibuntu.org/ maverick non-free free # medibuntu
deb http://download.virtualbox.org/virtualbox/debian maverick non-free
# deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu intrepid/
# deb http://www.avenard.org/files/ubuntu-repos lucid release

deb http://ppa.launchpad.net/shutter/ppa/ubuntu maverick main
#openbox https://launchpad.net/~k-belding/+archive
# deb http://ppa.launchpad.net/k-belding/ubuntu karmic main
# deb-src http://ppa.launchpad.net/k-belding/ubuntu karmic main
deb http://ppa.launchpad.net/arzajac/ppa/ubuntu maverick main

# PPA for Gert Kulyk (to fix system sound problem)
# deb http://ppa.launchpad.net/gkulyk/ubuntu lucid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/gkulyk/ubuntu karmic main #last is jaunty


# Tor


#Congruity and concordance
# deb http://ppa.launchpad.net/mathieu-tl/ppa/ubuntu lucid main

## deb http://ppa.launchpad.net/c-korn/vlc/ubuntu lucid main # disabled on upgrade to lucid




# Pidgin

# deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main

#Firefox




#Nvidia drivers


deb http://ppa.launchpad.net/pj-assis/ppa/ubuntu maverick main #Guvcview repo
deb-src http://ppa.launchpad.net/pj-assis/ppa/ubuntu maverick main #Guvcvew repo



deb http://ppa.launchpad.net/amsn-daily/ppa/ubuntu maverick main
# deb http://mirrors.dotsrc.org/getdeb/ubuntu maverick-getdeb apps
# deb-src http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps
```

---

### Post by coffeecat on 2010-11-14
> **Robbyx said:**
> I can't see the duplicate.

Nor can I. However, from your sources.list...

> **Robbyx said:**
> ```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb-src http://archive.canonical.com/ubuntu maverick partner
```

You only have the sources line and the ordinary deb line is missing. Compare with the same section from a default sources.list:

```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner
```You, or something, must have removed the deb line at some point. Check in the /etc/apt/sources.list.d/ folder to ensure there's not a duplicate there.

---

### Post by Robbyx on 2010-11-14
Thank you for checking my sources list. I have copied back the missing line. I have just run the update manager and it has not reported an error. I am hoping you have found the cause. 

Robin

---

