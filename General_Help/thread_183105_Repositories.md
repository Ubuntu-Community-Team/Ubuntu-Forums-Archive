---
title: "Repositories"
date: 2006-05-27
forum: General Help
---

### Post by PoisoN2003 on 2006-05-27
I recently tried adding 
these repositories 
```
deb http://seveas.ubuntulinux.nl/ breezy-seveas all
deb-src http://seveas.ubuntulinux.nl/ breezy-seveas all
```

Then i get this error when trying to update anything
> E: Malformed line 51 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Malformed line 51 in source list /etc/apt/sources.list (URI parse)
E: Unable to lock the list directory

My sources.list is 
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.lowvoice.nl/apt breezy main
deb-src http://wine.lowvoice.nl/apt breezy main

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://theli.free.fr/packages/breezy/ ./
## created by arniewinechanged
deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb http://wine.budgetdedicated.com/apt breezy main
deb free.linux.hp.com/~brett/seveas/freenx/ breezy-seveas freenx
 deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://de.archive.ubuntu.com/ubuntu hoary main universe multiverse restricted

```



So any idea what i have to do???

---

### Post by meng on 2006-05-27
Okay well looking at line 51 (thanks for making me count it out manually, btw :) ) you haven't prefaced the URI with [http://,](http://,) maybe that's throwing the error. I don't know for sure, it's just a guess but it can't hurt!

---

### Post by PoisoN2003 on 2006-05-27
thx it worked

---

### Post by gingermark on 2006-05-27
I would advise against using the "all" section of that repository, as it includes experimental metapackages and other stuff that could well pose problems.

See [https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages) for more details, but my advice would be to just use the sections for the software you need.

I would also use a mirror, as opposed to the home computer as you are currently doing (again, check that link for more info).

---

