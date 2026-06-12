---
title: "Synaptic Package Manger"
date: 2009-11-11
forum: General Help
---

### Post by Glyndog on 2009-11-11
I can not install or remove any applications and I get this error :

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

When i try sudo apt-get install -f  I get this :

The following NEW packages will be installed:
  build-essential dpkg-dev patch
0 upgraded, 3 newly installed, 0 to remove and 10 not upgraded.
27 not fully installed or removed.
Need to get 0B/662kB of archives.
After this operation, 1896kB of additional disk space will be used.


I hit Y then it says :

Media change: please insert the disc labeled
 'Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)'
in the drive '/cdrom/' and press enter


Now i presume this is the CD I used to install my Ubuntu which I got of a website for free. However when I put the CD in it just doesnt work, it just keeps saying 

Media change: please insert the disc labeled
 'Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)'
in the drive '/cdrom/' and press enter

Any help would be very helpful!

---

### Post by arnab_das on 2009-11-11
i think reloading the packages from the CD might solve ur problem.

---

### Post by sakubas on 2009-11-11
post here your sources.list file

```
cat /etc/apt/sources.list
```

---

### Post by Glyndog on 2009-11-11
am not sure how to reload from cd?

Here is the output of that command:

```
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ie.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ie.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ie.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ie.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ie.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ie.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by konqueror7 on 2009-11-11
try removing the first line and do,
```
sudo apt-get update
```

---

### Post by sakubas on 2009-11-11
First, comment de first line of the file:

```
....
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
....

```

then run:

```

sudo apt-get update
sudo apt-get install -f

```

---

### Post by Glyndog on 2009-11-11
ok thanks I cant do it because I do not have permission, erm, I am the owner of the computer how excatly do I edit this as root?

cheers.

---

### Post by konqueror7 on 2009-11-11
```
sudo gedit /etc/apt/sources.list
```

---

### Post by Glyndog on 2009-11-11
thanks it worked!

Thanks everyone for their help!

---

