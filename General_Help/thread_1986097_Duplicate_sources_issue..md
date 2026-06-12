---
title: "Duplicate sources issue."
date: 2012-05-24
forum: General Help
---

### Post by pierreyy on 2012-05-24
hey guys, 

i ran apt-get  and i got a duplicate sources issue 

the terminal output :

>   Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)  


Thanks in advance!!

---

### Post by skater40165 on 2012-05-24
Edit /etc/apt/sources.list and remove the duplicate source

---

### Post by pierreyy on 2012-05-24
> **skater40165 said:**
> Edit /etc/apt/sources.list and remove the duplicate source

thanks for the quick reply!!

---

### Post by skater40165 on 2012-05-24
NP please let me know if this worked if not I have a few other ideas.

---

### Post by jamaas on 2012-05-29
> **skater40165 said:**
> NP please let me know if this worked if not I have a few other ideas.

I get the same message, checked this file and there are no duplicates, doesn't even contain the references that pop up in the warning message.  Where else might they be?

Thanks

J

---

### Post by plucky on 2012-05-29
> **jamaas said:**
> I get the same message, checked this file and there are no duplicates, doesn't even contain the references that pop up in the warning message.  Where else might they be?

Thanks

J

Look in **/etc/apt/sources.list.d** for more .list files.

If you cannot find anything,open a terminal and post the output for ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
```

Good luck

---

### Post by jamaas on 2012-05-29
Thanks Plucky,

Did just that, had a look and I don't see any obvious duplicates, perhaps you can point them out.  The duplicate message is I'm getting is

=================

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


==========================
The output you requested is,


$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) precise universe
deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) precise multiverse
deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) precise-security main restricted
deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) precise-security universe
deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) precise-security multiverse

deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) precise-backports restricted main multiverse universe



$ cat /etc/apt/sources.list.d/*.list
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main
deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
# channel for the karmic (9.10) partner channel
# 
#:description:This channel contains the partner software for karmic
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb [http://ppa.launchpad.net/marutter/rrutter/ubuntu](http://ppa.launchpad.net/marutter/rrutter/ubuntu) precise main # disabled on upgrade to precise
# deb-src [http://ppa.launchpad.net/marutter/rrutter/ubuntu](http://ppa.launchpad.net/marutter/rrutter/ubuntu) precise main # disabled on upgrade to precise
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) precise main
deb-src [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) precise main
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main

---

### Post by Azdour on 2012-05-29
Hi,

In sources.list you have the line:

```
deb http://archive.canonical.com/ubuntu precise partner
```

And then it is repeated in the listing of files in cat /etc/apt/sources.list.d/*.list

```
deb http://archive.canonical.com/ubuntu precise partner
```

So there is a file in sources.list.d that contains this repeating line. Once you remove this then the duplication warning should go away.

---

### Post by jamaas on 2012-05-29
That worked !

Thanks

Jim 

> **Azdour said:**
> Hi,

In sources.list you have the line:

```
deb http://archive.canonical.com/ubuntu precise partner
```

And then it is repeated in the listing of files in cat /etc/apt/sources.list.d/*.list

```
deb http://archive.canonical.com/ubuntu precise partner
```

So there is a file in sources.list.d that contains this repeating line. Once you remove this then the duplication warning should go away.

---

### Post by pierreyy on 2012-06-20
> **skater40165 said:**
> NP please let me know if this worked if not I have a few other ideas.

sorry for the late reply... finals :P 

anw i found the duplicate in the sources.list and removed it... thank you so much!

---

