---
title: "update manager not working"
date: 2009-10-11
forum: General Help
---

### Post by Bogdanovist on 2009-10-11
My update manager tells me

```
current dist not found in meta-release file

```

My sources list looks like

```
deb http://ppa.launchpad.net/scipy/ppa/ubuntu intrepid main
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://sm.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb http://sm.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://sm.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://sm.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb http://sm.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb http://sm.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://ppa.launchpad.net/scipy/ppa/ubuntu intrepid main
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://sm.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://sm.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://sm.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://sm.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://sm.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://sm.archive.ubuntu.com/ubuntu/ intrepid-updates universe

```

I'm running 8.10

Any idea what is going wrong? I'd like to get this fixed so that I can upgrade to 9.04. At the moment the option to upgrade doesn't even appear in my update manager.

I am still getting updates that do seem to be installing, but there is obviously something wrong at some level. Not sure when or how this started unfortunately.

---

### Post by eric3_14159 on 2009-11-09
I don't know what's wrong, but especially if you're going to upgrade, maybe you could just back up that sources.list, and replace it for now with the original? Hopefully that will work.

Since I had to search a little to find it, here is the original (with thanks to [http://ubuntuforums.org/showpost.php?p=6335375&postcount=2](http://ubuntuforums.org/showpost.php?p=6335375&postcount=2) )

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
#deb http://archive.canonical.com/ubuntu intrepid partner
#deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

```

---

### Post by coffeecat on 2009-11-09
This link might help. It addresses Intrepid > Jaunty specifically, although it doesn't explain why /var/lib/update-manager/meta-release is faulty.

[https://help.ubuntu.com/community/UpgradeProblems](https://help.ubuntu.com/community/UpgradeProblems)

Interestingly, my Jaunty has no /var/lib/update-manager/meta-release at all, yet update manager is telling me that I can upgrade to Karmic.

By the way, I've found that googling the exact error message often finds a fix. In this case googling "current dist not found in meta-release file" and filtering the google search to the last year in the "options" link gave me that link as the 4th hit.

---

