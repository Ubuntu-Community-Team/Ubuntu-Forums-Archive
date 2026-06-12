---
title: "software updates"
date: 2010-10-06
forum: General Help
---

### Post by clairejaffa on 2010-10-06
i keep getting this message when doing updates

W:Failed to fetch [http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

any help would be appreciated :)

---

### Post by hhh on 2010-10-06
You added those sources to install some software, but it looks like you added the wrong repositories. There is no Maverick source there...
[http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/](http://ppa.launchpad.net/ferramroberto/extra/ubuntu/dists/)

What were you trying to install from there?

[https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid](https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid)

---

### Post by clairejaffa on 2010-10-06
i really cant remember :confused: im quite new to ubuntu and i was installing something and it came up with a box asking for the cd.i just want to get it back to installing the updates or should i do a clean install :( which i really dont want to do as i upgraded from 10.04 and it would mean losing everything i have.

---

### Post by andrewthomas on 2010-10-06
post the output of 

```
cat /etc/apt/sources.list
```

---

### Post by clairejaffa on 2010-10-06
michael@michael-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Beta i386 (20100901.1)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick restricted #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick restricted main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick restricted multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates restricted main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates restricted multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by oldos2er on 2010-10-06
You can disable the PPA via menus System, Administration, Synaptic Package Manager, Settings, Repositories, Other Software tab.

---

### Post by andrewthomas on 2010-10-06
That is regular

How about

```
ls /etc/apt/sources.list.d
```

---

### Post by clairejaffa on 2010-10-06
thanks everyone that did the trick :P:P 

not been using Ubuntu that long and the few problems i have had there is always an answer on this forum :smile:  very much appreciated.

---

