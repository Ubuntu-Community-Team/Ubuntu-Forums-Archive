---
title: "malformed line 59 in source list etc/apt/sources.list- Help appreciated!!"
date: 2011-08-23
forum: General Help
---

### Post by JazzPotato on 2011-08-23
Hello there forum!

There is a problem with my source list (apparently) I'm running 11.04 if that helps.
When I try to use apt-get install update for example, I get: "Malformed line 59 in source list etc/apt/sources.list"
The same error occurs when trying to access synaptic package manager, it tells me there is a malformed line and the list of sources cannot be read. 
This error prevents me from apt-getting anything, updating and i suspect it is affecting the software center too. :-(

Help would be appreciated!!!
Thanks

---

### Post by dave01945 on 2011-08-23
can you post a copy of your sources.list so we can see also if you can put it in code tags it makes it easier to read

---

### Post by JazzPotato on 2011-08-23
```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty restricted main
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty restricted main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates restricted main
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
deb http://gb.archive.ubuntu.com/ubuntu/ natty-proposed main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-proposed main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse
```

---

### Post by JazzPotato on 2011-08-23
I have attempted overwriting the sources.list file with a fresh one but it is read-only so i cannot change it. sudo nautilus may help?

---

### Post by dave01945 on 2011-08-23
> **JazzPotato said:**
> ```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty restricted main
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty restricted main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates restricted main
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
[B]deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner[/B]
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
deb http://gb.archive.ubuntu.com/ubuntu/ natty-proposed main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-proposed main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse
```

i would say try to remove the 2 lines i have highlighted with bold and see if that works to edit use

```
gksu gedit /etc/apt/sources.list
```

hopefully that helps

---

### Post by JazzPotato on 2011-08-23
Ah yes, i er.. obviously thought of that, i errr... just wanted to make sure that i was right.... :-)
Thank you!
How strange that that would work though...

---

### Post by ajgreeny on 2011-08-23
Open the file with ```
gksudo gedit /etc/apt/sources.list
``` which will give you root privileges, and add a # at the start of line 59 so that the system ignores it, or delete that line entirely.  The line 60 below is what it should have been, so there is no need to add anything else.

EDIT:
Whoops, I just noticed that the install is natty, but those two lines are for Lucid.

Your problem is now answered by dave01945 anyway,  so welcome to the forums.

---

