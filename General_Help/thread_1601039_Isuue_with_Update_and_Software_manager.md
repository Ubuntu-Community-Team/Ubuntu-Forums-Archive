---
title: "Isuue with Update and Software manager"
date: 2010-10-19
forum: General Help
---

### Post by geo20004 on 2010-10-19
My computer tried to run an update (I have it set up to do so automatically) however I got an error. Specifically, it said: 

Malformed line 53 in source list/ etc/apt/sources.list
Unable to lock repository

Any help to fix this problem is greatly apprecited.

---

### Post by sikander3786 on 2010-10-19
Please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by cogier on 2010-10-19
You need to check what is going on on line 53 of your sources.list file.

Use the following code in Terminal
```
sudo gedit /etc/apt/sources.list
```

Count down to line 53 and see if there is any obvious error. If you can't see anything post the line on the Forum here and someone may be able to help you correct it.

You will need to save the correction and try the update again.

---

### Post by geo20004 on 2010-10-19
Below are my results:


# deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://download.tuxfamily.org/gericom/libreoffice/](http://download.tuxfamily.org/gericom/libreoffice/)

---

### Post by 3rdalbum on 2010-10-19
> **geo20004 said:**
> 
deb [http://download.tuxfamily.org/gericom/libreoffice/](http://download.tuxfamily.org/gericom/libreoffice/)

That very last line is wrong - it should read:

```
deb http://download.tuxfamily.org/gericom/libreoffice /
```

Note the space between "libreoffice" and the final slash. Once you've made the alteration and saved your changes, run 'sudo apt-get update'.

In future, don't manually edit your sources.list by hand. Go to Applications > Ubuntu Software Center. Go to the Edit menu and go to Software Sources. Click the "Other Software" tab and the Add button, and type or paste your repository line into there. The Software Sources program will not let you add a malformed line and would have prevented your problem.

---

### Post by geo20004 on 2010-10-19
Thanks that solved it!

---

