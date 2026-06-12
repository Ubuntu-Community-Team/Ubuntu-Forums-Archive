---
title: "repository index problem"
date: 2009-08-10
forum: General Help
---

### Post by zozio32 on 2009-08-10
Hi

I am running ubuntu 9.04 on my laptop.
I am a recurrent error coming up when I'm trying to check if there is any update available from the "Update manager".
Here is the code of the error:

```
failed to fetch [http://ppa.launchpad.net/psyke83/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/psyke83/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

I guess I should change something in the 'Software Source' manager, but I am not sure to what it should be changed.

---

### Post by michy99 on 2009-08-10
Post your sources.list file.```
cat /etc/apt/sources.list
```

---

### Post by zozio32 on 2009-08-10
here are the result from the line of code you asked me to try:

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-proposed main multiverse universe restricted
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main multiverse universe restricted

# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu jaunty main # disabled on upgrade to jaunty
# deb-src http://ppa.launchpad.net/psyke83/ubuntu jaunty main # disabled on upgrade to jaunty
```

---

### Post by michy99 on 2009-08-10
I just checked and ppa.launchpad.net/psyke83 does not have a Jaunty repository, only Hardy and Intrepid. Either disable that repository or change it to Intepid.

---

### Post by zozio32 on 2009-08-10
thanks

the error don't show up anymore (I have change it to intrepid).

btw, from the list of sources you've seen, do I miss anything important, like some backports or other?

---

