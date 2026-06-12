---
title: "Synaptic Package Manger error"
date: 2010-11-18
forum: General Help
---

### Post by jmlynn on 2010-11-18
Hi,

Synaptic Package Manager failed with the following error:

E: Malformed line 55 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

With the error dialog as modal window, the Synaptic Package Manager main screen is disabled.  As soon as I click "OK" to close the error dialog, Synaptic Package Manager shuts down right away.

I don't know there is the "repository dialog" is to correct the problem as suggested.  Any suggestion on how to fix this problem?

Thanks!

Jeff

---

### Post by shashanksingh on 2010-11-18
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maveri$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe




just copy paste this in /etc/apt/sources.list and restart.
Add any specefic sources u need on it coz if it went till line 55 there must be a lot of them

---

### Post by plucky on 2010-11-18
> just copy paste this in /etc/apt/sources.list and restart.
Add any specefic sources u need on it coz if it went till line 55 there must be a lot of them 

Not good advice as his repository might not even relate to Maverick or India.It is better to get the OP to fix their sources.list

To OP,

Please post output of ```
cat /etc/apt/sources.list
``` so we can advise you how to correct the problem.

Good Luck

---

### Post by shashanksingh on 2010-11-18
> **plucky said:**
> Not good advice as his repository might not even relate to Maverick or India.It is better to get the OP to fix their sources.list

To OP,

Please post output of ```
cat /etc/apt/sources.list
``` so we can advise you how to correct the problem.

Good Luck

My bad...
Beginner here..
:P

---

### Post by jmlynn on 2010-11-18
I ended up "boldly" (:D as a relative newbie to ubuntu and my Unix skilld been tramped on by my clients' demand for Windows OS) take a copy of the archived version and rename it.  Then the system detected new updates and now I am home free.

Thanks everyone.  Appreciated!

Jeff

---

