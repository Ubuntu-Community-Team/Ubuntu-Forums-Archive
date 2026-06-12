---
title: "synaptic down"
date: 2010-03-14
forum: General Help
---

### Post by tongsengpakronilezat on 2010-03-14
hi, all
Just installed skype, as instructed in medibuntu, but failed. Then, everytime i run synaptic, it fails too. the message says : 
E: Type '--2010-03-14' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

anybody can offer me hands ? how should i repair that ?

---

### Post by stilling on 2010-03-14
open terminal > cat /etc/apt/sources.list

and post the reply

or see the line 1 that seems to have the error

---

### Post by mikewhatever on 2010-03-14
As the error says, you need to edit a line in /etc/apt/sources.list.d/medibuntu.list. Can you post the output of the following first:

head /etc/apt/sources.list.d/medibuntu.list

---

### Post by stilling on 2010-03-14
yes i`m sorry i didn`t look well sorry for that

---

### Post by tongsengpakronilezat on 2010-03-15
> **stilling said:**
> open terminal > cat /etc/apt/sources.list

and post the reply

or see the line 1 that seems to have the error

sorry, for the late response ( btw, i'm 7 hours away east of gmt ) :)

this is the result of the cat command :

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main

so the 1st line would be :

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

it is restricted, like it says in the error message. but, how should i repair this ? awaiting your reply,

very many thanks for the kind help . . .

regards,

---

### Post by tongsengpakronilezat on 2010-03-15
> **mikewhatever said:**
> As the error says, you need to edit a line in /etc/apt/sources.list.d/medibuntu.list. Can you post the output of the following first:

head /etc/apt/sources.list.d/medibuntu.list

this is the result :
--2010-03-14 18:03:30--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
Resolving [www.medibuntu.org]("http://www.medibuntu.org")... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80]("http://www.medibuntu.org%7C87.98.242.110%7C:80")... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-03-14 18:03:31 ERROR 404: Not Found.

then, what ?

---

### Post by stoneage on 2010-03-15
The problem is on the /etc/apt/sources.list.d/medibuntu.list file.

It appears to be for feisty, surely it should be for karmic? As far as I am aware feisty is no longer supported, which might explain the 404 error.

---

### Post by oldos2er on 2010-03-15
Run ```
gksu gedit /etc/apt/sources.list.d/medibuntu.list
```
Delete all the text, then add 
[B]deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free 
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free[/B]

Save and close the file, then run ```
sudo apt-get update
```

---

### Post by tongsengpakronilezat on 2010-03-15
> **oldos2er said:**
> Run ```
gksu gedit /etc/apt/sources.list.d/medibuntu.list
```Delete all the text, then add 
[B]deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free 
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free[/B]

Save and close the file, then run ```
sudo apt-get update
```

thank you very much. it's running now ( i mean, my synaptic ). thank you all for the help . . .

---

