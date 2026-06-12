---
title: "cant check for updates 11.04"
date: 2011-07-29
forum: General Help
---

### Post by mmsmc on 2011-07-29
when i open update manager, i click check for updates, than i get this:

W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/mavrick/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/mavrick/partner/source/Sources)  404  Not Found
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/mavrick/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/mavrick/partner/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

any suggestions?

thanks


I use ubuntu 11.04

---

### Post by jerrrys on 2011-07-29
try changing your download source first.

if that doesn't work, open a terminal and enter

sudo gedit /etc/apt/sources.list

and please post the results

---

### Post by drs305 on 2011-07-29
If you copied the entries "maverick" is misspelled in both instances.

You can manually check for typos with "gksu gedit /etc/apt/sources.list" or go into Synaptic or Software Sources and use the Edit button in Settings > Repositories > Other Software > Canonical Partners.

---

### Post by Dngrsone on 2011-07-29
If you are going through a firewall, then you need to fix your permissions.

---

### Post by mmsmc on 2011-07-29
here are the results of the command


# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Beta i386 (20110413)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) mavrick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) mavrick partner

---

### Post by jerrrys on 2011-07-29
ok drs305, how in the world did you know that!

anyhow, for th OP:

just comment out (#) the last two lines that have mavrick in them and you should be good to go.

---

### Post by drs305 on 2011-07-29
> **mmsmc said:**
> here are the results of the command


Last section .....


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) **[COLOR="Red"]mavrick[/COLOR]** partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) [COLOR="Red"]**mavrick**[/COLOR] partner

These have to be fixed via the methods I mentioned in my previous post. These should either be removed or changed to *natty*.

---

### Post by mmsmc on 2011-07-29
ok, thanks all that worked!

---

