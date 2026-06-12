---
title: "Ubuntu Software Center Not Working."
date: 2011-09-10
forum: General Help
---

### Post by RichardC400 on 2011-09-10
I have 11.04 and when i go into ubuntu software center and go into a category it searches, and searches, and searches some more, coming up with nothing apart from searching.

I tried
```
sudo apt-get update
```

and got

```

E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```

Can anyone help?

---

### Post by Rubi1200 on 2011-09-10
Hi,
please post the output of the following command:

```
cat /etc/apt/sources.list
```

Thanks.

---

### Post by faisal inayat on 2011-12-29
[SIZE=2]I also have same problem. RESULT IS HERE:







# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty universe
deb [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb-src [http://tm.archive.ubuntu.com/ubuntu/](http://tm.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
[/SIZE]

---

