---
title: "Update Manager Error"
date: 2009-07-21
forum: General Help
---

### Post by disco.sleeze on 2009-07-21
The last time Update Manager ran I got this message:

Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/sarge/main/binary-i386/Packages](ftp://ftp.nerim.net/debian-marillat/dists/sarge/main/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /debian-marillat/dists/sarge/main/binary-i386/Packages: No such file or directory  '
Some index files failed to download, they have been ignored, or old ones used instead.

I'm very new to Ubuntu and Linux in general, but do know hoe to search and haven't found a solution. I thank you in advance for your help.

---

### Post by synapsys on 2009-07-21
Don't know why your update manager is trying to get debian sarge updates... what version of ubuntu are you running?

Please post the contents of this file:

open a terminal (applications >> accessories >> terminal)
and type:
```
gedit /etc/apt/sources.list
```

---

### Post by WIGGMPk on 2009-07-21
Its telling you that the repository listed, does not exsit.

Double check the repository. I took a quick look at it, and it doesnt exsit. At least the full path doesnt exsit. However you added the repository (be it a tutorial/guide) you should double check to see if there is an updated one.


This doesnt exsit:
```
ftp://ftp.nerim.net/debian-marillat/dists/sarge/main/binary-i386/Packages
```

This does exsit:
```
ftp://ftp.nerim.net/
```

However that site does not contain a subdirectory called:
debian-marillat (or any of the child directories for that matter)

---

### Post by disco.sleeze on 2009-07-22
@synapsis: I am running Jaunty, 9.04. Here are the contents of the file per your request:

> # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

@WIGGMPk I am not sure how they got in my list then. Haha. Is it safe to remove that particular directory then?

---

### Post by WIGGMPk on 2009-07-22
I would remove it if you are certain you didnt add a repository.

Not sure how it got added, but its not usable because that repository is wrong/non-exsitant

---

### Post by disco.sleeze on 2009-07-23
Something new has popped up. I went to delete the bunk source from the file, and when I hit save it said I didn't have permission to edit the file.

I tried using the su command in terminal to change my login to root and try again, but when I entered my password it said "authentication failure".

I am the only user on this machine, and have made no changes to my password lately.:confused:

---

### Post by SecretCode on 2009-07-23
> **disco.sleeze said:**
> Something new has popped up. I went to delete the bunk source from the file, and when I hit save it said I didn't have permission to edit the file.

I tried using the su command in terminal to change my login to root and try again, but when I entered my password it said "authentication failure".

I am the only user on this machine, and have made no changes to my password lately.:confused:

You need to use **sudo <command>** ... Ubuntu doesn't enable **su**. (See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo))

---

