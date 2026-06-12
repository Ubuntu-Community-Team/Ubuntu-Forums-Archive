---
title: "software download problem."
date: 2011-01-12
forum: General Help
---

### Post by hijiz on 2011-01-12
Please help  I installed cairo dock and after that anythig realiting software synaptic, ubuntu software center, update manager) doesn't work when i try to install using terminal i get this mesage > E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
 
and yes I am root. please give me information on how to;
 a) delete cairo dock through terminal.
 b)fix whatever is wrong.

thanks in advance

---

### Post by wojox on 2011-01-12
Close out all you package managers. Maybe even reboot.

---

### Post by matt_symes on 2011-01-12
Hi

To remove cairo dock.

```
sudo apt-get remove cairo-dock
```

or 

```
sudo apt-get purge cairo-dock
```

to also remove configuration files as well.

First, when you try to install things through the terminal, synaptic pacakge manager, update manager and software centre are all closed ?

You are not currently updating the system in anyway ? Cron maybe ?

You may have an old lock kicking about. This can be deleted.

Kind regards

---

### Post by hijiz on 2011-01-13
ok so when i try to purge cairo dock i recieve this Reading package lists... Done
> Building dependency tree       
Reading state information... Done
E: Unable to locate package cario-dock
second no every thing is closed synaptic update manager and software center wont even open.
and i am in no way updating the system.
lastly i have no idea what cron is much less how to use it.

---

### Post by matt_symes on 2011-01-13
Hi

> **hijiz said:**
> ok so when i try to purge cairo dock i recieve this Reading package lists... Done

second no every thing is closed synaptic update manager and software center wont even open.
and i am in no way updating the system.
lastly i have no idea what cron is much less how to use it.

Sorry my Typo.

```
sudo apt-get purge cairo-dock
```

will purge cairo dock.

Have you tried a reboot?

Kind regards

---

### Post by hijiz on 2011-01-13
ok so some thing wierd also happened when everything started to fail. my  toolbarhas a little red error icon.when I klick on the little red icon  Update Manager opens loads about 3/4 and then this message apears saying
 > Could not initialize the pakage information
 An unresolvable problem occured while initializing the pakage information
 bla  bla bla
'E:Malformed line 52 in source list /etc/apt/sources.list (dist parse)' 

when i open synaptic it gives me this
>  E: Malformed line 52 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
and as i ve said before softwae center wont even open

---

### Post by matt_symes on 2011-01-15
Hi

Open a terminal and type 

```
cat /etc/apt/sources.list
``` 

Please post the output back here. You have a problem with your sources.list file.

Kind regards

---

### Post by matt_symes on 2011-01-15
For goodness sake. What is going on with the forums at the moment. _Another multiple post after the forums hung_

---

### Post by matt_symes on 2011-01-15
For goodness sake. What is going on with the forums at the moment. _Another multiple post after the forums hung_

---

### Post by matt_symes on 2011-01-15
For goodness sake. What is going on with the forums at the moment. _Another multiple post after the forums hung_

---

### Post by hijiz on 2011-01-16
this is the output
> # deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) jaunty main # disabled on upgrade to maverick
# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) jaunty main # disabled on upgrade to maverick
# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) jaunty main # disabled on upgrade to maverick
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) maverick
main ## Cairo-Dock-PPA-Stable
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-backports restricted main multiverse universe

---

### Post by oldos2er on 2011-01-17
Change line 52 to 

deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) maverick main

That should all be on one line. I'd removed the "## Cairo-Dock-PPA-Stable" too. It looks like the line formatting just got messed up somehow.

---

### Post by hijiz on 2011-01-17
ok so how do i do that?

---

### Post by matt_symes on 2011-01-17
Hi

Press ALT and F2 together and type

```
gksudo gedit
```

Navigate to the file and edit it.

Kind regards

---

### Post by hijiz on 2011-01-18
how do i navigate to the file? is it saved somewhere? 
Please fogive the fact im such a noob.

---

### Post by matt_symes on 2011-01-18
Hi

Press Alt and F2 together and type 

```
gksudo gedit
```

and enter your password

Select Open.

Select "file system" in the left hand pane.

Look for a folder called "etc" and double click on it.

Select a folder called "apt" and double click on it.

Look for a file called sources.list and select it.

You can edit it that way.

Kind regards

---

### Post by hijiz on 2011-01-18
thanks but the file is a read only i tried to change the permissions in properties but its blocked

---

### Post by oldos2er on 2011-01-18
Don't change permissions on the file. Using "gksu" elevates your user to having admin privileges needed to edit the file. Please run ```
gksu gedit /etc/apt/sources.list
``` in a terminal, and if there are any errors please post them here.

You might want to read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by matt_symes on 2011-01-18
Hi

> thanks but the file is a read only i tried to change the permissions in properties but its blocked

No offense, however it is better to follow instructions that will fix your problem ;)

Kind regards

---

