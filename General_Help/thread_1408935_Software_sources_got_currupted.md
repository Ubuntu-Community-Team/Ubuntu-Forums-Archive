---
title: "Software sources got currupted"
date: 2010-02-17
forum: General Help
---

### Post by abcuser on 2010-02-17
Hi,
I am using Ubuntu 9.10. I have added new PPA using a command, but this command got frozen. So I have closed terminal and reopen it.

Now I see "software sources" got corrupted. Please see attachments of System | Administration | Software Sources where all of the check-boxes are empty and and Other Software list is empty.

I have checked file /etc/apt/sources.list and there is the following text in it:
```

## See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
# CDROMs are managed through the apt-cdrom tool.

```
So all of the sources vanished.

Is there any way I can get this source list back?
Regards

---

### Post by Dies on 2010-02-17
Here's a stock one. ;)

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Beta i386 (20090929.2)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```

---

### Post by NightwishFan on 2010-02-17
If you did not have a lot of sources perhaps you could re-ad them yourself. You could also check the four Ubuntu ones, at the very least main.

---

### Post by abcuser on 2010-02-17
Hi,
I have restore Ubuntu from system backup and now everything is working well.

Just wondering why corruption appeared in the first place. Any idea? It looks there is some bug in adding new software source to /etc/apt/sources.list using command.
Thanks

---

### Post by t0p on 2010-02-17
> **abcuser said:**
> Hi,
Just wondering why corruption appeared in the first place. Any idea? It looks there is some bug in adding new software source to /etc/apt/sources.list using command.


Are you sure it's a *bug*?  Have a look on Launchpad, see if anyone else has reported this problem.  A search of this forum (using Google with *site:ubuntuforums.org* in search field) may also produce reports.

Another way to see if it's a bug is to try to recreate the problem.  Revert your sources.list file to its original state, then run the command again to add the PPA.  If this corrupts the sources.list again... it may be a bug.

---

