---
title: "cant open update manager or package manager"
date: 2012-10-06
forum: General Help
---

### Post by ssreesanth on 2012-10-06
i am unable to open update manager.

getting an error 

'E:Malformed line 50 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

---

### Post by claracc on 2012-10-06
As it is indicated in the error report, any line in /etc/apt/sources.list is malformed. Please, post your sources.list file and perhaps we can address de error.

---

### Post by ssreesanth on 2012-10-06
thanks for the quick reply... please find the source list below... before posting this thread i had done some research and might have changed some lines... but all in vain...

# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release i386 (20110720.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates restricted main multiverse universe
deb [http://ppa.launchpad.net/rubiojr/airvideo/ubuntu](http://ppa.launchpad.net/rubiojr/airvideo/ubuntu)[ yourdist] main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe main multiverse restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports universe main multiverse restricted

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by claracc on 2012-10-06
As I can see you have repositories belonging to two different releases: ubuntu lucid lynx and ubuntu precise pangolin.

What release do you have? ubuntu 10.04 or ubuntu 12.04.

Depending of what release you have, your sources.list file has to have the repositories belonging to this release and not to other.

All the repositories for lucid or all the repositories for precise.

I also see, you have duplicate lines as : deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner 

You have a messed sources.list file.

I recommend you use the gui in order to change it: In system tools, administration you choose sources software and tic or untick desired pakages.

Or you can use [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) in order to generate a valid sources.list

---

### Post by ssreesanth on 2012-10-06
hey,,

cant i just delete some lines and make all this proper...

---

### Post by claracc on 2012-10-06
Also, the number 50 line:

deb [http://ppa.launchpad.net/rubiojr/airvideo/ubuntu](http://ppa.launchpad.net/rubiojr/airvideo/ubuntu)[ yourdist] main

has a syntax error in [yourdist] you have to write precise or lucid ( the release you are running) without []

---

### Post by claracc on 2012-10-06
> **ssreesanth said:**
> hey,,

cant i just delete some lines and make all this proper...

Yes, you can edit the file and delete the duplicate lines, mantaining the debs for only one release (precise or lucid) and correct the wrong lines, but you have to be careful.

---

### Post by vasa1 on 2012-10-06
> **ssreesanth said:**
> hey,,

cant i just delete some lines and make all this proper...
+1 to claracc's suggestion to use the GUI.

Also, do you need the source code entries?

Oops! First post says OP **can't open** update manager.

---

### Post by ssreesanth on 2012-10-06
thanks man... i just replaced it with "lucid" and update manager is opening and the error is gone... well do u think i will have more problems as per th source list??

---

### Post by claracc on 2012-10-06
> **ssreesanth said:**
> thanks man... i just replaced it with "lucid" and update manager is opening and the error is gone... well do u think i will have more problems as per th source list??

You are welcome, but...I am a girl.

I don't know if you will have more problems with your sources.list. Have you deleted duplicate lines?, have you fixed the syntax error  in line 50?, have you the deb software packages for only one release (lucid or precise)?. All this three problems I think need to be fixed.

You can try if your system works now, running updates, if no errors, system works.

If you got fixed your problem, please mark the thread as solved with "thread tools" in the upper part of the page.

---

### Post by ssreesanth on 2012-10-06
alright "girl"

thanks.. will  mark it solved... will bother u if im in trouble again...

cheers!!!

---

