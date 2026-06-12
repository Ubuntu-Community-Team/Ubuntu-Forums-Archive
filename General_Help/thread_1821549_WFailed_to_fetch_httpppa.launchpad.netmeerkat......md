---
title: "W:Failed to fetch http://ppa.launchpad.net/meerkat....."
date: 2011-08-09
forum: General Help
---

### Post by Bart92 on 2011-08-09
Hi,

I need some help with the update manager in Ubuntu 11.04,
every time i try to update i get this..

[B]W:Failed to fetch [http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/source/Sources)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

, E:Some index files failed to download. They have been ignored, or old ones used instead.[/B]

pleas help :-k,

Thanks,

---

### Post by haqking on 2011-08-09
> **Bart92 said:**
> Hi,

I need some help with the update manager in Ubuntu 11.04,
every time i try to update i get this..

[B]W:Failed to fetch [http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/source/Sources)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

, E:Some index files failed to download. They have been ignored, or old ones used instead.[/B]

pleas help :-k,

Thanks,


Are you using an old sources.list or upgraded from 10.10.

they refer to meerkat which is 10.10 and you are now using 11.04.

gksudo gedit /etc/apt/sources.list

and place a # at the beginning of any lines which are no longer pertinent to your version.

---

### Post by Bart92 on 2011-08-09
> **haqking said:**
> Are you using an old sources.list or upgraded from 10.10.

they refer to meerkat which is 10.10 and you are now using 11.04.

gksudo gedit /etc/apt/sources.list

and place a # at the beginning of any lines which are no longer pertinent to your version.

Thanks :)

But strange i am not upgraded from 10.10 to 11.04 i have used the 11.04 CD
How can i possibly have a old source list ?

---

### Post by Bart92 on 2011-08-09
The meerkat sources are not in the sources.list :confused:

---

### Post by Bart92 on 2011-08-09
> **haqking said:**
> Are you using an old sources.list or upgraded from 10.10.

they refer to meerkat which is 10.10 and you are now using 11.04.

gksudo gedit /etc/apt/sources.list

and place a # at the beginning of any lines which are no longer pertinent to your version.

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

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

---

### Post by haqking on 2011-08-09
> **Bart92 said:**
> # deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

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

in update manager go to settings and other software.  remove the ticks which reference your problem PPA's

---

### Post by Bart92 on 2011-08-09
> **haqking said:**
> in update manager go to settings and other software.  remove the ticks which reference your problem PPA's

What do you mean with ticks?

And the problem is getting bigger ](*,)

[B]W:Failed to fetch [http://ppa.launchpad.net/Bart/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/Bart/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/Bart/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/Bart/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/source/Sources)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/source/Sources)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

, E:Some index files failed to download. They have been ignored, or old ones used instead.
[/B]

---

### Post by haqking on 2011-08-09
> **Bart92 said:**
> What do you mean with ticks?

And the problem is getting bigger ](*,)

[B]W:Failed to fetch [http://ppa.launchpad.net/Bart/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/Bart/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/Bart/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/Bart/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/source/Sources)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/source/Sources)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

, E:Some index files failed to download. They have been ignored, or old ones used instead.
[/B]

I mean remove the ticks as in a tick next to a source.
  Scroll down in other software and you should see the ppa links to which you refer
see image

---

### Post by Bart92 on 2011-08-09
> **haqking said:**
> I mean remove the ticks as in a tick next to a source.
  Scroll down in other software and you should see the ppa links to which you refer
see image

Thanks a lot :)

---

### Post by haqking on 2011-08-09
> **Bart92 said:**
> Thanks a lot :)


no problem, you are welcome

---

