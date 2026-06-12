---
title: "update manager and syaptic cannot initialize"
date: 2009-07-24
forum: General Help
---

### Post by Blu Fox on 2009-07-24
I cannot open my update manager/synaptic/add and remove utilities.

I get this bug error:
'E:Type 'wget' is not known on line 55 in source list /etc/apt/sources.list, E:The list of sources could not be read.

I don't really think I've been screwing around with the sources list. 

PS: I'm a first time linux newbie.

---

### Post by drs305 on 2009-07-24
Blu Fox, Welcome to the Ubuntu forums!

There is an error on line 55 of your sources.list  

Open for editing and look at line 55, which is where the cursor should be positioned:
```

gksudo gedit +55 /etc/apt/sources.list

```

All sources.list lines must begin with a # symbol or "deb". If the error on this line isn't obvious post it here and we can look at it for you.

---

### Post by Blu Fox on 2009-07-24
Alright I'll just post the sources list
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://cu.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://cu.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cu.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://cu.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://cu.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://cu.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://cu.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://cu.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://cu.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://cu.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://cu.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://cu.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://cu.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://cu.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
wget http://packages.dfreer.org/7572013D.gpg -O-
 sudo apt-key add -
sudo apt-get update
echo "deb http://packages.dfreer.org gutsy main" | sudo tee -a /etc/apt/sources.list
## wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
sudo apt-get update
```I'm pretty sure the second to last line is the problematic line, but I have absolutely no idea how to fix it :(

---

### Post by michy99 on 2009-07-24
All of the following needs to be removed from the file.```
wget http://packages.dfreer.org/7572013D.gpg -O-
 sudo apt-key add -
sudo apt-get update
echo "deb http://packages.dfreer.org gutsy main" | sudo tee -a /etc/apt/sources.list
## wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
sudo apt-get update
```Open it for editing with```
gksudo gedit /etc/apt/sources.list
```Remove the problem lines, save the file and then run```
sudo apt-get update
```

---

### Post by Blu Fox on 2009-07-24
Whao, thanks man! 

Didn't really thought the other lines would cause problems. 
And do expect me to come on here a lot, I'm very new to this

---

