---
title: "Can' t open Synaptic Package Manager"
date: 2010-04-07
forum: General Help
---

### Post by diamaltho on 2010-04-07
An error occurred
The following details are provided: 
E: Malformed line 8 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem,
E:_cache->open() failed, please report

I get this error message every time I try to open Synaptic Package Manager or enter a [sudo] command in the terminal. 
1. Where is the "repository" ?
2. How can I fix the problem ?

Please, help me I' m new to Ubuntu...

---

### Post by bolucpap on 2010-04-07
Could you post the output when you type: ```
cat /etc/apt/sources.list
```, please?
Also, which version of Ubuntu do you have installed?

---

### Post by diamaltho on 2010-04-07
I' m using Edubuntu 9.04

---

### Post by s.fox on 2010-04-07
Hello,

Can you please open a terminal and enter the following command:

```
cat /etc/apt/sources.list
```

Please post the output :)

-Silver Fox

---

### Post by 3rdalbum on 2010-04-07
> **diamaltho said:**
> 
E: Malformed line 8 in source list /etc/apt/sources.list (dist parse)

The eighth line in the '/etc/apt/sources.list' file is incorrect. Open up the file as root, like so:

```
gksudo gedit /etc/apt/sources.list
```

Find the bit that is wrong, and 'comment it out' (put a hash symbol # before the line)

Save your changes and run:

```
sudo apt-get update
```

And in future, don't manually modify the sources.list file. Instead, go to System > Administration > Software Sources in order to add and remove repositories. It doesn't let you put in an invalid/malformed entry into the sources list.

---

### Post by etcall911 on 2010-04-07
im also having the same problem.

everytime i run a sudo update it will appear as this:
'<?xml' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list


sudo  cat /ept/apt/sources.list shows
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic restricted main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates restricted main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

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
# deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security restricted main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security restricted main universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

# deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

---

### Post by mine070 on 2010-04-07
Pretty Much what it is saying is that a repo on the list if Malformed. Goto the line and tell me what it says.

---

### Post by diamaltho on 2010-04-07
# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main universe multiverse restricted
deb [http://netbook-remix.archive.canonical.com/updates/](http://netbook-remix.archive.canonical.com/updates/) jaunty-athens public

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/updates/](http://netbook-remix.archive.canonical.com/updates/) jaunty-athens public
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty 
maindeb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main

---

### Post by diamaltho on 2010-04-07
Thank you I found it!
I tried to install VLC Media Player, and on the readme file, said that I had to add the two last lines at the file, as first step.
Although, because this didn' t help me, can you tell me how to install VLC ?

---

### Post by TheSqueak on 2010-04-07
> **diamaltho said:**
> # /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main universe multiverse restricted
deb [http://netbook-remix.archive.canonical.com/updates/](http://netbook-remix.archive.canonical.com/updates/) jaunty-athens public

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/updates/](http://netbook-remix.archive.canonical.com/updates/) jaunty-athens public
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty 
maindeb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main

the first part of that last line should be ```
deb-src
```
and not ```
maindeb-src
```

---

### Post by sandyd on 2010-04-07
also, on the second last line, add "main" to the end (without the quotes)

---

