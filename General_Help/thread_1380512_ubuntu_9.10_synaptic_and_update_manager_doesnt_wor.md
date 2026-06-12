---
title: "ubuntu 9.10 synaptic and update manager doesnt work"
date: 2010-01-13
forum: General Help
---

### Post by giuseppe321 on 2010-01-13
I got this error message today when i ran sudo update 

E: Type 'See' is not known on line 2 in source list /etc/apt/sources.list
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list

and i cant burn dvd with brasero also my sis760 doesnt work on this 

im trying to switch back to windows but i need to copy the image to a dvd
 but brasero doesnt work and when ever i use the software center i see nothing under the categories

is this os always so glitchy???

---

### Post by stoneage on 2010-01-13
For problem #1 I think your sources.list is wrong. Did you edit it manually?

Can you post the output of ```
gksudo gedit /etc/apt/sources.list
```

For problem #3 I'm not surprised as that seems to be a Windows driver..... What graphics card do you use?

---

### Post by running_rabbit07 on 2010-01-13
> **giuseppe321 said:**
> is this os always so glitchy???

Just for you, but hopefully we can get that fixed for ya.:)

---

### Post by giuseppe321 on 2010-01-13
heres the output






deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
 See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
 newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

 Major bug fix updates produced after the final release of the
 distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 team. Also, please note that software in universe WILL NOT receive any
 review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 team, and may not be under a free licence. Please satisfy yourself as to 
 your rights to use the software. Also, please note that software in 
 multiverse WILL NOT receive any review or updates from the Ubuntu
 security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

 Uncomment the following two lines to add software from the 'backports'
 repository.
 N.B. software from this repository may not have been tested as
 extensively as that contained in the main release, although it includes
 newer versions of some applications which may provide useful features.
 Also, please note that software in backports WILL NOT receive any review
 or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

 Uncomment the following two lines to add software from Canonical's
 'partner' repository.
 This software is not part of Ubuntu, but is offered by Canonical and the
 respective vendors as a service to Ubuntu users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

---

### Post by stoneage on 2010-01-13
Yep, you need to comment out all the plain text so it looks more like this:-
> ## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

Do that with every line that doesn't begin with deb. Save it, then open System -> Administration -> Software Sources and enable only the repositories you need to download packages from.

---

### Post by giuseppe321 on 2010-01-13
cant i just copy your whole source code bcuz for sum reason it just deleted its self

---

### Post by giuseppe321 on 2010-01-13
this is how it looks like now

##deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic ##main restricted
 ##See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
##newer versions of the distribution.


##Major bug fix updates produced after the final release of the
##distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted ##universe

##N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
##team. Also, please note that software in universe WILL NOT receive any
##review or updates from the Ubuntu security team.

##N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
##team, and may not be under a free licence. Please satisfy yourself as to 
##your rights to use the software. Also, please note that software in 
##multiverse WILL NOT receive any review or updates from the Ubuntu
##security team.

##Uncomment the following two lines to add software from the 'backports'
##repository.
 ##extensively as that contained in the main release, although it includes
##newer versions of some applications which may provide useful features.
##Also, please note that software in backports WILL NOT receive any review
##or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted ##universe

##Uncomment the following two lines to add software from Canonical's
##'partner' repository.
##This software is not part of Ubuntu, but is offered by Canonical and the
##respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted  ##universe
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse main universe ##restricted

---

### Post by running_rabbit07 on 2010-01-13
> **giuseppe321 said:**
> cant i just copy your whole source code bcuz for sum reason it just deleted its self



```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release  (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```

---

### Post by stoneage on 2010-01-13
Try this one, though obviously I can't guarantee it will work for you. You should still edit your Software Sources.

[http://www.pasteall.org/10285](http://www.pasteall.org/10285)

Type ```
gksudo gedit
``` into a Terminal and save it to /etc/apt as sources.list




EDIT - I don't use 32 bit, but I edited the file the original poster uploaded.

---

### Post by giuseppe321 on 2010-01-13
that fix the update package problem but can you tell me the reason why nothing shows up in the software center??

---

### Post by stoneage on 2010-01-13
It could be because your system was unable to access any of the repositories.

Try ```
sudo apt-get update
``` then ```
sudo apt-get upgrade
```


If that doesn't help you could try a reboot.

---

### Post by giuseppe321 on 2010-01-13
oops on more problem the error is shorter now this is what it sais

E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list

---

### Post by stoneage on 2010-01-13
```
gksudo gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
``` 

Probably it is similar to the sources.list error. Just comment out the plain text and resave it.

Post it up if you are unsure.

---

### Post by giuseppe321 on 2010-01-13
Thank you the source is working now    :D:D

---

### Post by stoneage on 2010-01-13
Cool.

Is the driver for the graphics card?

---

