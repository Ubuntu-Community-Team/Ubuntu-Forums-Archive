---
title: "error in update manager"
date: 2010-08-24
forum: General Help
---

### Post by oleink on 2010-08-24
I keep getting this error when trying to update but I know it is a bug and has been filed as a bug report but the reporter marked it as solved without saying how it was solved... :(

```
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by clhsharky on 2010-08-24
oleink

Is your (cdrom with Ubuntu 10.04'Lucid Lynx') still ticked in Software Sources?

Sharky

---

### Post by oleink on 2010-08-24
> **clhsharky said:**
> oleink

Is your (cdrom with Ubuntu 10.04'Lucid Lynx') still ticked in Software Sources?

Sharky

Its comented out in the file as far as I know. And quick question can you give me a list of the ppa's I NEED I think I deleted one on accident (stupid mouse haha)

---

### Post by oleink on 2010-08-24
Yeah I double checked and it's commented out and unclicked in software sources

---

### Post by gbestrada on 2010-08-25
try reinstalling the update manager.
go to : system > synaptic package manager > and in the search box write update manager.
then right click "update manager " and choose "mark for reinstallation " .
then click on the apply icon .and it will reinstall and hopefully remove the bug.

I hope this helps you.;)

---

### Post by oleink on 2010-08-25
> **gbestrada said:**
> try reinstalling the update manager.
go to : system > synaptic package manager > and in the search box write update manager.
then right click "update manager " and choose "mark for reinstallation " .
then click on the apply icon .and it will reinstall and hopefully remove the bug.

I hope this helps you.;)

That doesn't re-add the ppa.  Can someone who knows which ppa lines I absolutely need for ubuntu list the ppa lines and I'll re-add the one I'm missing

---

### Post by oleink on 2010-08-25
can anyone list the required ppas for ubuntu??

---

### Post by wojox on 2010-08-25
Here oleink try this [Ubuntu Sources List Generator]("http://repogen.simplylinux.ch/")

What does this return?

```
cat /etc/apt/sources.list
```

---

### Post by oleink on 2010-08-25
> **wojox said:**
> Here oleink try this [Ubuntu Sources List Generator]("http://repogen.simplylinux.ch/")

What does this return?

```
cat /etc/apt/sources.list
```

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

Thanks for the link! :)

---

### Post by oleink on 2010-08-26
That's my output

---

### Post by plucky on 2010-08-26
> can anyone list the required ppas for ubuntu?? 

There are no required PPA's for Ubuntu.

---

### Post by oleink on 2010-08-26
> **plucky said:**
> There are no required PPA's for Ubuntu.

I just meant the standard ppa update ppas

---

