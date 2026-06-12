---
title: "Update Manager won't open"
date: 2011-02-09
forum: General Help
---

### Post by kp goin on 2011-02-09
Can't open Update Manager. Attached is the error report:

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu./>>/etc/apt/sources.list' is not known on line 59 in source list /etc/apt/sources.list' "

I suspect the 'E:Type 'http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu./>>/etc/apt/sources.list' reference might be connected to a download of driver for a Samsung printer, copier, scanner - Samsung United Driver.

I am also including a sources.list problem that also references this  'E:Type 'http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu./>>/etc/apt/sources.list':

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

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
http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu./>>/etc/apt/sources.list

echo [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu./]("http://mambo.kuhp.kyoto-u.ac.jp/%7Etakushi/ubuntu./")
deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu]("http://mambo.kuhp.kyoto-u.ac.jp/%7Etakushi/ubuntu") ./
# deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu]("http://mambo.kuhp.kyoto-u.ac.jp/%7Etakushi/ubuntu") ./

I am running 10.10 Maverick Meerkat

Help.
kp goin

---

### Post by kellemes on 2011-02-09
Comment out the lines with the mambo stuff.. and try again.

Edit: You probably should keep **deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./** in order to get your printer-driver updates.
The lines starting with **hhtp **and **echo **should be removed (or commented out with #).

---

### Post by kp goin on 2011-02-10
How do I "comment out the lines"?
Where do I go to do that?

---

### Post by plucky on 2011-02-10
> **kp goin said:**
> How do I "comment out the lines"?
Where do I go to do that?

Open **Applications > Accessories > Terminal** and input ```
gksudo gedit /etc/apt/sources.list
``` Then put a # in front of ```
http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu./>>/etc/apt/sources.list

echo http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu./
```

Save the file and exit.

Good Luck

---

### Post by kp goin on 2011-02-12
I don't understand the "SOLVED" thing so I figured this was safest way to make sure my "Thanks" to kellemes and plucky got to them.
Thank you for solving this issue, there are others, but this one is SOLVED.
 
...but, in the end, it was the education that is more appreciated.

---

