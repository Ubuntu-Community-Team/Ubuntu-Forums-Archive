---
title: "Can't update anything. UpdateManager&amp;Synaptic."
date: 2009-08-19
forum: General Help
---

### Post by soundf on 2009-08-19
It fails to update in my ubuntu system.
I upgraded my Hardy into Jaunty and at first had no problems, 
but now I can't update and download things from Synaptic(what really bothers me).

When i try to update, the status is always "Failed".
I saw that it might be a source list problem, so here it is:

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://il.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://il.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://il.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://il.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://il.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://il.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://il.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://il.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://il.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

Please help me.
Thanks.

---

### Post by philinux on 2009-08-19
Open a terminal and use this. Post back the errors.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by soundf on 2009-08-19
edited

---

### Post by DonnieP on 2009-08-19
> **soundf said:**
> It fails to update in my ubuntu system.
I upgraded my Hardy into Jaunty and at first had no problems, 
but now I can't update and download things from Synaptic(what really bothers me).

When i try to update, the status is always "Failed".
I saw that it might be a source list problem, so here it is:

I was having similar problems today, but after running the update about the fifth time it was finally able to download all the updates just a few minutes ago (US repository).

---

### Post by soundf on 2009-08-19
trying update again and again doesn't help for me.
Does someone know what should I do so I could update again?
Maybe I need to change to a different repository(If yes, how?)?

Thanks.

---

### Post by philinux on 2009-08-19
System>admin>software sources

Change the server to main.

---

### Post by soundf on 2009-08-19
Still doesn't work..
For United States Server, too.

Edit:
I clicked "Select Best Server", and it works for a server in another country.. Well, it works so thanks for helping.

---

### Post by ekwang on 2009-08-19
Refer Korean server address..

```

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp.daum.net/ubuntu/ jaunty main restricted
deb-src http://ftp.daum.net/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.daum.net/ubuntu/ jaunty-updates main restricted
deb-src http://ftp.daum.net/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb **http://ftp.daum.net/ubuntu/** jaunty universe
deb-src **http://ftp.daum.net/ubuntu/** jaunty universe
deb **http://ftp.daum.net/ubuntu/** jaunty-updates universe
deb-src **http://ftp.daum.net/ubuntu/** jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb **http://ftp.daum.net/ubuntu/** jaunty multiverse
deb-src **http://ftp.daum.net/ubuntu/** jaunty multiverse
deb **http://ftp.daum.net/ubuntu/** jaunty-updates multiverse
deb-src **http://ftp.daum.net/ubuntu/** jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://kr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://kr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

---

