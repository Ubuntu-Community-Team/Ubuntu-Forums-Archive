---
title: "Malformed line 58 in source list"
date: 2011-03-07
forum: General Help
---

### Post by haste28 on 2011-03-07
hey i recently couldnt open software center so i opened synpatic package manager only t o get this error
E: Malformed line 58 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

please i need help im still a bit of a noob and have no idea what to do 
thanks in advance

---

### Post by TeoBigusGeekus on 2011-03-07
```
gksu gedit /etc/apt/sources.list
```
Can you post us the contents of the file?

---

### Post by haste28 on 2011-03-07
here is the entire sources.list please help i hope the text isn't to much 
thanks in advanced
[HTML]
# 
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main #Added by software-properties

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://eg.archive.ubuntu.com/ubuntu/ maverick main restricted multiverse
deb-src http://eg.archive.ubuntu.com/ubuntu/ maverick main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://eg.archive.ubuntu.com/ubuntu/ maverick-updates main restricted multiverse
deb-src http://eg.archive.ubuntu.com/ubuntu/ maverick-updates main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://eg.archive.ubuntu.com/ubuntu/ maverick universe
deb http://eg.archive.ubuntu.com/ubuntu/ maverick-updates universe

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
deb http://eg.archive.ubuntu.com/ubuntu/ maverick-backports main universe restricted multiverse
# deb-src http://eg.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security main universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://eg.archive.ubuntu.com/ubuntu/ maverick-proposed main universe restricted multiverse

#Eternal Lands package repository
deb http://ppa.launchpad.net/pjbroad/ppa/ubuntu maverick main
deb http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu maverick
deb-src http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu maverick 
[/HTML]

---

### Post by TeoBigusGeekus on 2011-03-07
Well it seems that the problem is the line
```
deb http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu maverick
```
in your sources.list. Can you confirm that this is the 58th line?
Did you add the Eternal Lands repository by hand or by other means?

EDIT: According to [this]("http://www.lotrolinux.com/download.php") page, it should be
```
deb http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu maverick main
```
Make the correction, save and
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by haste28 on 2011-03-08
aw !@#$ i did what you said and apperantly line 58 is fine now but when i ran the terminal code you gave me it gave me this 
```

E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```i hope you you can help me again i feel like a major noob
thanks in advance

never mind i did it myself now software center and synaptic package manager work like a charm thanks for your help

---

