---
title: "Software Update Problems"
date: 2012-01-10
forum: General Help
---

### Post by Michaeldnr on 2012-01-10
Hi Everyone,

I have had this problem for quite some time now and it"s really starting to get on my nerves.

Whenever I try to update using the Software Update I get the following error:

W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release)  Unable to find expected entry 'sound/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/oneiric/Release](http://za.archive.ubuntu.com/ubuntu/dists/oneiric/Release)  Unable to find expected entry 'sound/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/oneiric-security/Release](http://za.archive.ubuntu.com/ubuntu/dists/oneiric-security/Release)  Unable to find expected entry 'sound/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release](http://za.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release)  Unable to find expected entry 'sound/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

My package information hasn't been updated in 42days so it's really getting serious. I've tried to modify the sources.list file but with no effect.

Here's my sources.list file:

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric main universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric-security main universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric-security main universe #Added by software-properties
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric sound
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric sound #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security sound main
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric-security sound #Added by software-properties
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric-updates sound main universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric-updates sound main universe #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric-updates restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric-security restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric-security restricted

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free

Please Help!!!

---

### Post by plucky on 2012-01-10
> W:Failed to fetch [http://security.ubuntu.com/ubuntu/di...curity/Release](http://security.ubuntu.com/ubuntu/di...curity/Release) Unable to find expected entry 'sound/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

This is because of ```

deb http://za.archive.ubuntu.com/ubuntu/ oneiric sound
deb-src http://za.archive.ubuntu.com/ubuntu/ oneiric sound #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ oneiric-security sound main
deb-src http://za.archive.ubuntu.com/ubuntu/ oneiric-security sound #Added by software-properties
deb http://za.archive.ubuntu.com/ubuntu/ oneiric-updates sound main universe
deb-src http://za.archive.ubuntu.com/ubuntu/ oneiric-updates sound main universe #Added by software-properties
```


You do not neeed the "deb-src" lines and the word sound should not be in any of those lines.


> deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

That line needs to be commented out using the # symbol at the start of the line.

An alternative would be to generate a new sources.list [Here](http://repogen.simplylinux.ch/) and replace your current sources.list with a clean list.

You should probably also add the multiverse repository.

Good Luck

---

### Post by Michaeldnr on 2012-01-10
Thank you Plucky! It worked. I'm still a bit of a n00b at linux so the help is much appreciated!:popcorn:

---

