---
title: "Help w/ Terminal and Software Center"
date: 2011-06-03
forum: General Help
---

### Post by alexduhgreat on 2011-06-03
Hey guys im kind of a noob at this so bear with me pls
My software center has stopped working so I tried Synaptic which doesnt even open so I tried 
```
[sudo apt-get update
```
and got the following

E: Type '&#8220;deb' is not known on line 60 in source list /etc/apt/sources.list
E: The list of sources could not be read.

so I give you my source list...any help would be greatly appreciated.
Thanks!


# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty main restricted
deb-src [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-updates main restricted
deb-src [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty universe
deb-src [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty universe
deb [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-updates universe
deb-src [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty multiverse
deb-src [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty multiverse
deb [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-updates multiverse
deb-src [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-security main restricted
deb-src [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-security main restricted
deb [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-security universe
deb-src [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-security universe
deb [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-security multiverse
deb-src [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
&#8220;deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main&#8221;

---

### Post by matt_symes on 2011-06-03
Hi

Open a terminal and type 

```
sudo nano /etc/apt/sources.list
```Enter your password. It will not be echoed to the screen.

Remove the last lin that says..

&#8220;deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main&#8221;

Press ctrl + o to save and then ctrl + x to exit.

Then type

```
sudo apt-get update
```Kind regards

---

