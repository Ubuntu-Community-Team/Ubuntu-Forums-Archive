---
title: "Update information is outdated, but no updates available??"
date: 2010-11-27
forum: General Help
---

### Post by ibrahim.k on 2010-11-27
Hi

I am getting an error message telling me that update information is outdated in a time there is no updates available!

please tell me how to fix this,
more details in the link.
 [http://www.freeuploadimages.org/images/hcq594bm7ih9u13lt95.png](http://www.freeuploadimages.org/images/hcq594bm7ih9u13lt95.png)

---

### Post by plucky on 2010-11-27
> **ibrahim.k said:**
> Hi

I am getting an error message telling me that update information is outdated in a time there is no updates available!

please tell me how to fix this,
more details in the link.
 [http://www.freeuploadimages.org/images/hcq594bm7ih9u13lt95.png](http://www.freeuploadimages.org/images/hcq594bm7ih9u13lt95.png)

Open a terminal and run ```
sudo apt-get update
sudo apt-get upgrade
```

If that doesn't work, post output of ```
cat /etc/apt/sources.list
```

Good Luck

---

### Post by ibrahim.k on 2010-11-27
Thank you very much but it didn't work,

ibrahim@ibrahim-HP-Pavilion-dv6-Notebook-PC:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

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

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main
ibrahim@ibrahim-HP-Pavilion-dv6-Notebook-PC:~$

---

### Post by plucky on 2010-11-27
> Thank you very much but it didn't work,

Were there any errors given by the two commands?
If so, can you post what they were.

You sources.list look ok.

Are you using any sort of proxy?

---

### Post by ibrahim.k on 2010-11-27
Sometimes I use proxy, but now i am not using anything, direct internet connection
output of sudo apt-get update

[http://paste.ubuntu.com/537039/](http://paste.ubuntu.com/537039/)

---

### Post by ibrahim.k on 2010-11-27
I have deleted tor project from the sources and the error message is gone!
Thank you very much I will mark this topic as solved. :)

---

