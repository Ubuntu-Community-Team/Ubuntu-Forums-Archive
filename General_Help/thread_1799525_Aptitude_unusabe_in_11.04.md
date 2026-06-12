---
title: "Aptitude unusabe in 11.04"
date: 2011-07-07
forum: General Help
---

### Post by Cadeyrn on 2011-07-07
Since 11.04 was released, I've used it in Gnome and now also KDE, and this problem is in both. Aptitude is completely unusable.

The main issue is that when downloading packages, it disconnects every minute if not every half a minute, making package installing a very hard process and making the configuration of a new OS take days (just to install 1GB of packages). Ontop of the disconnections, aptitude doesn't even want to go full speed when it IS connected.

The other issues involve repositories. Whether it's the official Ubuntu package servers, ANY of its many mirrors, or even my own custom PPAs, connecting to ANY repository when I reload my packages is a hit-or-miss, and it's completely impossible to get them all in one refresh (in fact, I don't think I've been able to access the main server since upgrading. Ever. I've been on the US server). This makes installing all of my packages take even LONGER. Also, to add insult to injury, the list files in /var/lib/apt/lists constantly corrupt themselves and make themselves unusable, ESPECIALLY the PPA lists (anything that uses launchpad has to be disabled at all times unless I have to update its program, or else I have to delete those list files every day).

Googling any of these issues separately gets me nowhere, so I'm making a topic, and it better not be the millionth topic I've made here that never got solved.

P.S. The problem can't be my router or modem because my brother runs aptitude just fine on his 11.04 laptop. This issue is within my computer.

EDIT: Oewh. I meant apt-get. You mean they aren't the same program with two ways to run them? Yes, apt-get is the problemed one. I never actually type "aptitude" into the Terminal. As a consequence, Synaptic and KPackageKit and any other apt-get-using program is messed up as well.

---

### Post by JC Cheloven on 2011-07-07
Aptitude seems to have little sense lately, and I think it's being abadoned in favour of the latest versions of apt-get. Command line syntax is similar.

If you don't have a special reason to use aptitude, I'd suggest to try apt-get and see if it works as expected for you.

> 
I'm making a topic, and it better not be the millionth topic I've made here that never got solved.
213 at most :)

---

### Post by wildmanne39 on 2011-07-07
Hi, I have read that apt-get is preferred that is why aptitude is not installed be default.

---

### Post by oldos2er on 2011-07-07
> **wildmanne39 said:**
> Hi, I have read that apt-get is preferred that is why aptitude is not installed be default.

Aptitude was dropped from the CD due to space issues; it works as well as it ever did for me.

OP: Do other package managers e.g. Software Center or Synaptic have the same issues?

---

### Post by Cadeyrn on 2011-07-08
Oewh. I meant apt-get. You mean they aren't the same program with two ways to run them? Yes, apt-get is the problemed one. I never actually type "aptitude" into the Terminal. As a consequence, Synaptic and KPackageKit and any other apt-get-using program is messed up as well.

---

### Post by wildmanne39 on 2011-07-08
> **Cadeyrn said:**
> Oewh. I meant apt-get. You mean they aren't the same program with two ways to run them? Yes, apt-get is the problemed one. I never actually type "aptitude" into the Terminal. As a consequence, Synaptic and KPackageKit and any other apt-get-using program is messed up as well.Hi, maybe it is your source list if is it that messed up. Put these two command in a terminal one at a time
```
cat /etc/apt/sources.list
```
```
ls /etc/apt/sources.list.d/
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by kanishkdudeja on 2011-07-08
If u need to install aptitude, you can install it by:  

```
sudo apt-get install aptitude
```

---

### Post by Cadeyrn on 2011-07-08
Here's the terminal output:


```
jimi@Death-Book:~$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427)]/ natty main restricted
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Beta amd64 (20110413.1)]/ natty main restricted
deb http://ubuntu-archives.mirror.nexicom.net/ natty restricted main
#Addedby software-properties
deb-src http://ubuntu-archives.mirror.nexicom.net/ natty restricted main multiverse universe

deb http://ubuntu-archives.mirror.nexicom.net/ natty-security main restricted
#Addedby software-properties
deb-src http://ubuntu-archives.mirror.nexicom.net/ natty-security restricted main multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu-archives.mirror.nexicom.net/ natty-updates restricted main
#Addedby software-properties
deb-src http://ubuntu-archives.mirror.nexicom.net/ natty-updates restricted main multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu-archives.mirror.nexicom.net/ natty universe
deb http://ubuntu-archives.mirror.nexicom.net/ natty-updates universe
deb http://ubuntu-archives.mirror.nexicom.net/ natty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu-archives.mirror.nexicom.net/ natty multiverse
deb http://ubuntu-archives.mirror.nexicom.net/ natty-updates multiverse
deb http://ubuntu-archives.mirror.nexicom.net/ natty-security multiverse















deb http://packages.medibuntu.org/ natty free non-free
deb-src http://packages.medibuntu.org/ natty free non-free
deb http://ppa.launchpad.net/gfire/gfire/ubuntu/ natty main
deb-src http://ppa.launchpad.net/gfire/gfire/ubuntu/ natty main
deb http://ppa.launchpad.net/lazka/ppa/ubuntu/ natty main
deb-src http://ppa.launchpad.net/lazka/ppa/ubuntu/ natty main
deb http://ppa.launchpad.net/n-muench/vlc/ubuntu/ natty main
deb-src http://ppa.launchpad.net/n-muench/vlc/ubuntu/ natty main
deb http://ppa.launchpad.net/rufustfirefly/dolphin-emu/ubuntu/ natty main
deb-src http://ppa.launchpad.net/rufustfirefly/dolphin-emu/ubuntu/ natty main
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ natty main
deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ natty main
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ natty main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ natty main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ natty main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ natty main
deb http://ppa.launchpad.net/wii.sceners.linux/wiithon-1.1/ubuntu/ natty main
deb-src http://ppa.launchpad.net/wii.sceners.linux/wiithon-1.1/ubuntu/ natty main
deb http://security.ubuntu.com/ubuntu/ natty-security restricted main multiverse universe
deb http://winswitch.org/ natty main
deb-src http://winswitch.org/ natty main

deb http://archive.getdeb.net/ubuntu/ natty-getdeb apps
deb-src http://archive.getdeb.net/ubuntu/ natty-getdeb apps

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ natty-security main restricted
deb http://security.ubuntu.com/ubuntu/ natty-security universe
deb http://security.ubuntu.com/ubuntu/ natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu/ natty partner
deb-src http://archive.canonical.com/ubuntu/ natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu/ natty main
deb-src http://extras.ubuntu.com/ubuntu/ natty main


jimi@Death-Book:~$ ls /etc/apt/sources.list.d
jimi@Death-Book:~$ 
```


As you can see, there's nothing in sources.list.d, which makes no sense because the Canadian server (US went down too) and most of my custom PPAs are loaded and I'm installing their apps as we speak.

EDIT: Whoops. When I said that "makes no sense" statement, I had sources.list.d confused with the /var/lib/apt/lists folder. I don't know what I'm talking about with sources.list.d.

---

### Post by oldos2er on 2011-07-08
aptitude and apt-get are two separate programs. I got into the habit of preferring aptitude because at the time I started using Ubuntu, it was thought to handle package removal a bit more cleanly than apt-get.

---

