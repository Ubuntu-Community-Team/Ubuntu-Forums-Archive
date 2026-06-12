---
title: "Source List Problem"
date: 2010-08-25
forum: General Help
---

### Post by vonpatrick on 2010-08-25
Hi, newbie with the whole Linux - Ubuntu stuff. I've only been at it three days and managed to screw something up. I was trying to install the AWN dock from a step by step guide when I realized I messed up something. I can no longer open Synaptic Package Manager or the Update manager. I get the following message from both...

E: Type 'sudo' is not known on line 59 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

After trying to do some research to find a way to solve the problem without having to ask the forum first, I discovered this is a common problem, but its usually not "sudo" thats screwing up line 59. Any help would be most appreciated. I was loving ubuntu before I messed it up. And I still want to install a dock someday. :(

---

### Post by Charlietje on 2010-08-25
can you post the result of:

```
cat /etc/apt/sources.list
```

---

### Post by vonpatrick on 2010-08-25
> **Charlietje said:**
> can you post the result of:

```
cat /etc/apt/sources.list
```

Yes I can. Pasted your code into the terminal and got the following...

> cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) feisty main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) feisty main
sudo gedit /etc/apt/sources.list
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-
Dock-Stable 

---

### Post by howefield on 2010-08-25
Open a terminal and type

```
gksudo gedit /etc/apt/sources.list
```

scroll down to the line that reads "sudo gedit /etc/apt/sources.list" and remove it, save the file and reload your software sources.

Job done.

---

### Post by gandaran on 2010-08-25
> deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) feisty main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) feisty main
sudo gedit /etc/apt/sources.list
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
vonpatrick
AWN was already in the Ubuntu repositories, there was no need to add any extras repositories, that AWN repository with the AWN trunk version is only recommended for users that don't have a 3D video card, if you video card supports 3D effects don't install it, install only the regular AWN version that is in the Ubuntu repositories.
also you added the hardy and fiesty repositories which are wrong for you Ubuntu version, you should have chosen the right "lucid" repositories

---

### Post by vonpatrick on 2010-08-25
> **howefield said:**
> Open a terminal and type

```
gksudo gedit /etc/apt/sources.list
```scroll down to the line that reads "sudo gedit /etc/apt/sources.list" and remove it, save the file and reload your software sources.

Job done.

After doing as instructed, this started to appear instead...

>  'E:Type 'Dock-Stable' is not known on line 62 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

---

### Post by plucky on 2010-08-25
> deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-
Dock-Stable 

Should be ```
deb http://repository.glx-dock.org/ubuntu lucid cairo-dock ## Cairo-Dock-Stable
```

Edit the file and put that line all on one line.

Good Luck

---

### Post by vonpatrick on 2010-08-25
> **plucky said:**
> Should be ```
deb http://repository.glx-dock.org/ubuntu lucid cairo-dock ## Cairo-Dock-Stable
```Edit the file and put that line all on one line.

Good Luck

Still getting this...

> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'Dock-Stable' is not known on line 61 in source list /etc/apt/sources.list, E:The list of sources could not be read.'  

---

### Post by TwoEars on 2010-08-25
Run ```
gksudo gedit
``` then replace the text with > # deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid main ## cairo dock

Save, now try.

---

### Post by plucky on 2010-08-25
> **vonpatrick said:**
> Still getting this...

Post the new sources.list file and use [noparse]```

```[/noparse] blocks instead of [noparse]> [/noparse] as that preserves the formatting of the text.

---

### Post by vonpatrick on 2010-08-25
> **plucky said:**
> Post the new sources.list file and use [noparse]```

```[/noparse] blocks instead of  as that preserves the formatting of the text.

Oh, okay, here ya go.

```
vonpatrick@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
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
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports restricted main multiverse universe
deb http://ppa.launchpad.net/reacocard-awn/ubuntu feisty main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu feisty main
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
Dock-Stable
deb http://repository.glx-dock.org/ubuntu lucid cairo-dock ## Cairo-Dock-Stable
 
```

Btw, thank you to everyone for trying to help me solve this. :KS

---

### Post by plucky on 2010-08-25
```
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports restricted main multiverse universe
deb http://ppa.launchpad.net/reacocard-awn/ubuntu feisty main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu feisty main
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
[color=red]Dock-Stable[/color]
deb http://repository.glx-dock.org/ubuntu lucid cairo-dock ## Cairo-Dock-Stable
```


Can you not see that Dock-Stable is still in the list which I have highlighted in red.You should edit the file with the command ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of every line that doesn't have **lucid** in the line.

Or delete everything and copy and paste the sources.list that Twoears posted.

Why are you mixing repositories? Feisty is no longer supported.

Good luck

---

### Post by vonpatrick on 2010-08-25
> **plucky said:**
> ```
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports restricted main multiverse universe
deb http://ppa.launchpad.net/reacocard-awn/ubuntu feisty main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu feisty main
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
[COLOR=red]Dock-Stable[/COLOR]
deb http://repository.glx-dock.org/ubuntu lucid cairo-dock ## Cairo-Dock-Stable
```
Can you not see that Dock-Stable is still in the list which I have highlighted in red.You should edit the file with the command ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of every line that doesn't have **lucid** in the line.

Or delete everything and copy and paste the sources.list that Twoears posted.

Why are you mixing repositories? Feisty is no longer supported.

Good luck

I mixed things earlier on when I wasn't sure what I was doing. It took me a bit to learn coding and what all everything means in open source. I'm getting a hang of it. But the good news is everything seems to be fixed and back to normal! Thank you so much for your help! 

NOW...what should I should to PROPERLY Install AWN?

---

### Post by howefield on 2010-08-26
> **vonpatrick said:**
> It took me a bit to learn coding and what all everything means in open source.

Editing a text file isn't coding :-) 

> NOW...what should I should to PROPERLY Install AWN?

Did you have something against the version in the Ubuntu repository ? Load up Applications > Ubuntu Software Centre and type avant in the search field.

Avant Window Navigator should come up first in the list, click the install button.... the rest should be fairly self explanatory ?

---

### Post by surya.shah1414 on 2011-02-18
E: Type '“deb' is not known on line 65 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


i have also this problem, i need a solution,

---

### Post by plucky on 2011-02-19
> **surya.shah1414 said:**
> E: Type '“deb' is not known on line 65 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


i have also this problem, i need a solution,

Welcome to the Forum

This thread is already marked as [Solved],you should start your own Thread and post the output from a terminal of ```
cat /etc/apt/sources.list
``` to get a better response.

Or get a Moderator to move it by using the "Report Abuse" button.

Good Luck

---

