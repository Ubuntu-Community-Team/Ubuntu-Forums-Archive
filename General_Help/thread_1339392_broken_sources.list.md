---
title: "broken sources.list"
date: 2009-11-27
forum: General Help
---

### Post by Kohary on 2009-11-27
I have the following problems and have no idea what to do...

Can't update, it is not working
Synaptic package manager is not working too

This is the message when I want to update:
E: Malformed line 48 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

PLEASE HELP MEEEE....is it possible to repair or I have to reinstall my ubuntu 9.10?

---

### Post by Virtual Liberty on 2009-11-27
Show us the contents of [COLOR=DarkOrange]/etc/apt/sources.list[/COLOR].

---

### Post by A.S. on 2009-11-27
Hello,

have you checked the line 48 in your file /etc/apt/sources.list?

Would you like to post the file or the part around line 48?

---

### Post by aysiu on 2009-11-27
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cat /etc/apt/sources.list
``` and then paste the output back here.

---

### Post by Kohary on 2009-11-27
The biggest problem is...I can't even open sources.list

---

### Post by Kohary on 2009-11-27
Here it is....

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb http:ppa.launpad.net/awn-testing/ubuntu Jaunty
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) Jaunty
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
scuderia@Acer:~$

---

### Post by Virtual Liberty on 2009-11-27
```
deb httppa.launpad.net/awn-testing/ubuntu Jaunty

```

Remove this line, save the file and upon updating Aptitude database everything should work.

---

### Post by aysiu on 2009-11-27
Paste this command into the terminal: ```
gksudo gedit /etc/apt/sources.list
``` That should open the file up in a text editor. Then change the following line ```
deb httppa.launpad.net/awn-testing/ubuntu Jaunty
``` to ```
deb http://**p**pa.laun**ch**pad.net/awn-testing/ubuntu Jaunty
``` and save the file and close the text editor.

---

### Post by Virtual Liberty on 2009-11-27
> **aysiu said:**
> ```
deb http://ppa.launchpad.net/awn-testing/ubuntu Jaunty
``` and save the file and close the text editor.

Is there a specific reason for not using [COLOR=DimGray]main[/COLOR] at the end of this line ?

---

### Post by Kohary on 2009-11-27
How can I remove that line?
if I type etc/apt/sources.list  it says Permission denied

---

### Post by Virtual Liberty on 2009-11-27
> **Kohary said:**
> How can I remove that line?
if I type etc/apt/sources.list  it says Permission denied

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Kohary on 2009-11-27
So I have decide do to delete the following...

deb http:razz:pa.launpad.net/awn-testing/ubuntu Jaunty
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) Jaunty
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
scuderia@Acer:~$


AND IT'S WORKING..absolutely everything.

THANK YOU GUYS!!!!!!!!!!!!!!!!!!!:D

---

