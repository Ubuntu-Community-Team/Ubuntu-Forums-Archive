---
title: "Failed to load package list"
date: 2012-07-26
forum: General Help
---

### Post by jeffbilling on 2012-07-26
I received this message can someone help please.

---

### Post by dino99 on 2012-07-26
its kind of useless message , reload it (probably due to index not yet rebuilt when you hit "reload" icon)

but your sources.list seems needing some cleaning

sudo gedit /etc/apt/sources.list

---

### Post by jeffbilling on 2012-07-26
Thanks dino99 I have looked at source list and 'commented out' some duplicate entries.
I am still getting this error

---

### Post by plucky on 2012-07-27
> **jeffbilling said:**
> Thanks dino99 I have looked at source list and 'commented out' some duplicate entries.
I am still getting this error

Remove all of the .list files using ```
sudo rm /var/lib/apt/lists/* -vf
``` as one is left over from the previous problem and reload them with ```
sudo apt-get update
```

Good Luck

---

### Post by jeffbilling on 2012-07-28
> **plucky said:**
> Remove all of the .list files using ```
sudo rm /var/lib/apt/lists/* -vf
``` as one is left over from the previous problem and reload them with ```
sudo apt-get update
```

Good Luck
Thanks Plucky I have done as suggested and received this message after running apt-get update. I haven't run it a second time.

[B]Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems[/B]
jeffery@jeffery-desktop:~$ 

so it is looking much better. Not sure exactly what to do now.

---

### Post by plucky on 2012-07-28
> Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner _binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Open a terminal and post output for ```
cat /etc/apt/sources.list
```

---

### Post by jeffbilling on 2012-08-02
Sorry for delay have been sick for a few days. I hope this is what yoiu wanted
Jeff


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main universe multiverse restricted


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
##  deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
##  deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
##   deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise multiverse
##   deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates multiverse
##   deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
##   deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
##  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
##  deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
##  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main #Third party developers repository
## deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
##  deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib

---

### Post by plucky on 2012-08-02
That looks ok.

The Partner Repository might be located in the /etc/apt/sources.list.d/ directory

```
cat /etc/apt/sources.list.d/*.list
``` should show you the entries in that directory.

Delete one of them and then run the two commands I gave earlier.

Good Luck

---

### Post by jeffbilling on 2012-08-08
Many thanks plucky. Everything seems to be working fine.

---

