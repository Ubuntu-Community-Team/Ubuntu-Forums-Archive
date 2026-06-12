---
title: "Reading Package lists - Bus error"
date: 2010-08-07
forum: General Help
---

### Post by wwwbrowse on 2010-08-07
When I do :- sudo apt-get update

I get:- Reading Package lists... 0%

then:- Bus error

I have tried changing software sources and sudo apt-get -f install
, but no change.

Any help greatly appreciated.

---

### Post by inameiname on 2010-08-07
Have you changed your sources.list any? What does it output:

In the terminal:

gksu gedit /etc/apt/sources.list

---

### Post by inameiname on 2010-08-07
I found this thread, maybe it'll help:

[http://ubuntuforums.org/showthread.php?p=2070840](http://ubuntuforums.org/showthread.php?p=2070840)

---

### Post by wwwbrowse on 2010-08-07
> **inameiname said:**
> Have you changed your sources.list any? What does it output:

In the terminal:

gksu gedit /etc/apt/sources.list

I have tried changing sources. the output of the above is :-

# deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Release Candidate amd64 (20100419.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse

---

### Post by inameiname on 2010-08-07
Looks just fine. Guess that's not the issue.

Have you tried the solution proposed in that thread I mentioned:

That for that dude, there was something wrong with one of the files in ***/var/cache/apt/*** and he fixed things by moving the two *.bin files that were causing him woes to a backup directory and then everything was OK? Just one idea. Other than that, I'm afraid that's beyond my expertise.

---

### Post by wwwbrowse on 2010-08-07
> **inameiname said:**
> I found this thread, maybe it'll help:

[http://ubuntuforums.org/showthread.php?p=2070840](http://ubuntuforums.org/showthread.php?p=2070840)

this solved my problem.

many thanks!

---

### Post by inameiname on 2010-08-07
Sweet. 

Oh, and make sure you mark this thread as solved when you get a chance so it might help others with a similar issue.

---

