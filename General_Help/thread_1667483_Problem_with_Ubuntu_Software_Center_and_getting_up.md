---
title: "Problem with Ubuntu Software Center and getting updates!"
date: 2011-01-14
forum: General Help
---

### Post by MelvinCD7 on 2011-01-14
I was trying to install the Jdownloader in my computer. i couldn find it in the Ubuntu Software Center so I downloaded the .DEB from Internet, when I clicked for opening the application the Ubuntu Software Center start opening but it never open!

also there's a problem with the updates :

E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I'm a new ubuntu user!

---

### Post by wilee-nilee on 2011-01-14
Run this command in the Ubuntu terminal and post the whole text, in code tags. To get code tags click on the **(#)** in the reply panel and paste the text in between.
```
gksudo cat /etc/apt/sources.list
```

---

### Post by papibe on 2011-01-14
I can't help you with that error, since I also struggled to install jdownloader from different sources (including a ppa). The one that finaly worked for me was the very same script is available at JDownloader.org

I hope it helps.

BTW, you need to install Java first in order to run JDownloader.

---

### Post by MelvinCD7 on 2011-01-14
> **wilee-nilee said:**
> Run this command in the Ubuntu terminal and post the whole text, in code tags. To get code tags click on the **(#)** in the reply panel and paste the text in between.
```
gksudo cat /etc/apt/sources.list
```

Here you Go!


melvindc7@melvindc7-AO532h:~$ gksudo cat /etc/apt/sources.list

(gksudo:4096): Gtk-WARNING **: Theme directory  of theme Azenis Icons has no size field

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

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
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by MelvinCD7 on 2011-01-15
Solved!!!!! the problem was an space in the line 59! thanks you all guys!

---

### Post by MelvinCD7 on 2011-01-15
Solved!!!!! the problem was an space in the line 59! thanks you all guys!

---

### Post by MelvinCD7 on 2011-01-15
The problem is solved was a miss SPACE in the line 59.. thanks you all guys

---

### Post by techunit on 2011-01-15
Please mark thread as solved

---

