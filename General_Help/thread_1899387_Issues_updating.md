---
title: "Issues updating"
date: 2011-12-23
forum: General Help
---

### Post by Dadof4 on 2011-12-23
I keep getting errors when I try to update, this is what I get in the details of the error. 

> W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.40 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.40 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.40 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.40 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.40 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.40 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.40 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.40 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.I'm using Ubuntu 11.10 x64 and I do not know how to fix the error. It appears to me that these are old repositories but I cannot remove them. Ideas?

---

### Post by plucky on 2011-12-23
> **Dadof4 said:**
> I keep getting errors when I try to update, this is what I get in the details of the error. 

I'm using Ubuntu 11.10 x64 and I do not know how to fix the error. It appears to me that these are old repositories but I cannot remove them. Ideas?

It is trying to access the Karmic Repositories which are closed.

Please post output from the terminal for ```
cat /etc/apt/sources.list
```


Good Luck

---

### Post by Dadof4 on 2011-12-23
Thank you for the help so quickly. I'm new to this and I'm learning! Here is the output:

> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-updates main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-security main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-security universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-security multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-proposed restricted main multiverse universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-proposed restricted main multiverse universe #Added by software-properties
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main #Third party developers repository
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-backports restricted main multiverse universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) oneiric-backports restricted main multiverse universe #Added by software-properties

---

### Post by plucky on 2011-12-23
Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of ```
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://archive.canonical.com/ubuntu karmic partner
```

Then run ```
sudo apt-get update
``` and see if you get the same error.

Good Luck

---

### Post by philinux on 2011-12-23
Open a terminal and use.

gksu gedit /etc/apt/sources.list

Either put a # in front of the karmic lines or delete them.

Save the file the run

sudo apt-get update && sudo apt-get upgrade

---

### Post by Dadof4 on 2011-12-23
> steve@steve-desktop:~$ sudo apt-upgrade
[sudo] password for steve: 
sudo: apt-upgrade: command not found

The error has seemed to stop though.

---

### Post by philinux on 2011-12-23
> **Dadof4 said:**
> The error has seemed to stop though.

Doh. apt-get upgrade

---

### Post by Dadof4 on 2011-12-23
Ok I tried that and this is what I get. 


> steve@steve-desktop:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I appreciate your patience with me. I'm very green when it comes to this, last time I messed with code was Pascal.....(yes, I'm old)

---

### Post by plucky on 2011-12-23
> **Dadof4 said:**
> Ok I tried that and this is what I get. 

> steve@steve-desktop:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 


I appreciate your patience with me. I'm very green when it comes to this, last time I messed with code was Pascal.....(yes, I'm old)

You need to use sudo

```
sudo apt-get upgrade
```

---

### Post by Dadof4 on 2011-12-23
Got it! 0 upgrades. :)

Thanks!

---

