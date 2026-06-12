---
title: "An unresolvable problem occurred while initializing the package information."
date: 2011-06-22
forum: General Help
---

### Post by proggy on 2011-06-22
hello 

i need help with this
An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'son/experimental/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/adilson-experimental-natty.list'
thank you

---

### Post by wildmanne39 on 2011-06-22
> **proggy said:**
> hello 

i need help with this
An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'son/experimental/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/adilson-experimental-natty.list'
thank youHi, type this command in a terminal
```
cat /etc/apt/sources.list
```and this one to one at a time 
```
ls /etc/apt/sources.list.d/
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by proggy on 2011-06-22
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-updates multiverse

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

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

---

### Post by proggy on 2011-06-22
proggy@proggy-Aspire-M3910:~$ ls /etc/apt/sources.list.d/
adilson-experimental-maverick.list.distUpgrade
adilson-experimental-maverick.list.save
adilson-experimental-natty.list
adilson-experimental-natty.list.save
ferramroberto-extra-natty.list
ferramroberto-extra-natty.list.save
google-chrome.list
google-chrome.list.save
google-earth.list
google-earth.list.save
ppa-ppa-natty.list
ppa-ppa-natty.list.save
rvm-smplayer-natty.list
rvm-smplayer-natty.list.save
stebbins-handbrake-releases-natty.list
stebbins-handbrake-releases-natty.list.save
tualatrix-ppa-natty.list
tualatrix-ppa-natty.list.save
proggy@proggy-Aspire-M3910:~$

---

### Post by wildmanne39 on 2011-06-22
Hi, open update manager and go to settings then look for updates and see if prerelease updates or experimental is checked and uncheck it then reload updates and see if that fixes it. and uncheck backport if checked.

---

### Post by proggy on 2011-06-22
sorry no can do 
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'son/experimental/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/adilson-experimental-natty.list'

---

### Post by wildmanne39 on 2011-06-22
> **proggy said:**
> proggy@proggy-Aspire-M3910:~$ ls /etc/apt/sources.list.d/
adilson-experimental-maverick.list.distUpgrade
adilson-experimental-maverick.list.save
adilson-experimental-natty.list
adilson-experimental-natty.list.save
ferramroberto-extra-natty.list
ferramroberto-extra-natty.list.save
google-chrome.list
google-chrome.list.save
google-earth.list
google-earth.list.save
ppa-ppa-natty.list
ppa-ppa-natty.list.save
rvm-smplayer-natty.list
rvm-smplayer-natty.list.save
stebbins-handbrake-releases-natty.list
stebbins-handbrake-releases-natty.list.save
tualatrix-ppa-natty.list
tualatrix-ppa-natty.list.save
proggy@proggy-Aspire-M3910:~$
Hi, I took a second look at this file and I would delete all the experimental ones out of this list.

---

### Post by proggy on 2011-06-22
how do i modify the list that i got with this command 
ls /etc/apt/sources.list.d/

---

### Post by wildmanne39 on 2011-06-22
> **proggy said:**
> how do i modify the list that i got with this command 
ls /etc/apt/sources.list.d/Hi, open synaptic if it will let you, if not I guess you will have to report it as a bug. After you have synaptic open go to settings, repositories,software and see if those ppa's are listed if so uncheck them and while you are there look at updates and follow the directions about what should be uncecked from my previous post.

---

### Post by proggy on 2011-06-22
na you seen i can `t open synaptic 
thanks any ways
hopefully someone else can help

---

### Post by plucky on 2011-06-22
> **proggy said:**
> na you seen i can `t open synaptic 
thanks any ways
hopefully someone else can help

Delete the file with ```
sudo rm /etc/apt/sources.list.d/adilson-experimental-natty.list
``` as the information it contains is corrupt.

Or post output of ```
cat /etc/apt/sources.list.d/adilson-experimental-natty.list
``` so we can see what it contains.


Good Luck

---

### Post by proggy on 2011-06-22
proggy@proggy-Aspire-M3910:~$ cat /etc/apt/sources.list.d/adilson-experimental-natty.list
son/experimental/ubuntu natty main # disabled on upgrade to natty
rm: cannot remove `/etc/apt/sources.list.d/adilson-experimental-natty.list': No such file or directory

---

### Post by plucky on 2011-06-22
> rm: cannot remove `/etc/apt/sources.list.d/adilson-experimental-natty.list': No such file or directory 

Did you run the "sudo rm" command?

Post output of ```
ls /etc/apt/sources.list.d/
```

---

### Post by dFlyer on 2011-06-22
> **proggy said:**
> proggy@proggy-Aspire-M3910:~$ cat /etc/apt/sources.list.d/adilson-experimental-natty.list
son/experimental/ubuntu natty main # disabled on upgrade to natty
rm: cannot remove `/etc/apt/sources.list.d/adilson-experimental-natty.list': No such file or directory

Start Nautilus as so: gksu nautilus. Navigate to you /etc/apt/soucres.list.d/ folder and try to delete from there the adilson-experimental-natty.list.

---

### Post by proggy on 2011-06-22
woke up this morning refreshed re-did all the instructions here deleted the corrupt repo line and voila
Thank you all!

---

### Post by wildmanne39 on 2011-06-22
> **proggy said:**
> woke up this morning refreshed re-did all the instructions here deleted the corrupt repo line and voila
Thank you all!Hi, your welcome would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by jweaver28 on 2011-06-24
I had the same problem. I followed the instructions in [http://computerandu.wordpress.com/tag/ubuntu-11-04/](http://computerandu.wordpress.com/tag/ubuntu-11-04/) and then this thread, and the 13 outstanding natty updates of the last 3 days just installed nicely. I had been worried about firefox not updating because I knew the firefox 4 to 5 upgrade in windows was really a security package. FYI, I didn't have experimental packages selected in sources, and the link above told me to disable the lists, so the checkboxes for 3rd party sources etc were empty, but I deleted all the old meerkat (10.10) ubuntu and medibuntu packages as potential sources, and that seemed to resolve the problem.

---

