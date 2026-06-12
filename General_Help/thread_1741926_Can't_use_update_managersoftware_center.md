---
title: "Can't use update manager/software center"
date: 2011-04-28
forum: General Help
---

### Post by emaloley on 2011-04-28
Hello! I'm new to Linux. When I go to run the update manager, I get this message:

E:Malformed line 59 in source list/etc/apt/sources.list(dist parse)

I believe this error is also affecting other parts of my system. Any help would be appreciated! Thanks..:)

---

### Post by plucky on 2011-04-28
> **emaloley said:**
> Hello! I'm new to Linux. When I go to run the update manager, I get this message:

E:Malformed line 59 in source list/etc/apt/sources.list(dist parse)

I believe this error is also affecting other parts of my system. Any help would be appreciated! Thanks..:)

Welcome to the forum.

Open a terminal (**Applications > Accessories > Terminal**)

and post the output of ```
cat /etc/apt/sources.list
```

Good Luck

---

### Post by emaloley on 2011-04-28
Thank you for your assistance! Here are the results:

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner

---

### Post by plucky on 2011-04-28
```
deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner
```

Those lines should not be in the list.

To edit the file use ```
gksudo gedit /etc/apt/sources.list
``` and delete the two lines.Save the file and then run ```
sudo apt-get update
``` to see if the problem goes away.

Good Luck

---

### Post by emaloley on 2011-04-28
YES!!!! It worked. Thanks very much for your help. I do have another problem (which when trying to fix is how I ran into the one we just solved). Should I start a new thread or post it on here? Thanks again for your help!!:)

---

### Post by plucky on 2011-04-28
> **emaloley said:**
> YES!!!! It worked. Thanks very much for your help. I do have another problem (which when trying to fix is how I ran into the one we just solved). Should I start a new thread or post it on here? Thanks again for your help!!:)

If it is nothing to do with Update Manager/Software Centre,then it is best to start another thread with a Title that relates to the problem,so that anyone that can help will do so.

You can also mark this thread as **[Solved]** using the [color=red]Thread Tools[/color] at the top of the page.

Good Luck

---

