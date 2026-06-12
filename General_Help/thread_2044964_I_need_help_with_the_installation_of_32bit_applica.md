---
title: "I need help with the installation of 32bit applications in my 64 bit Ubuntu 12.04"
date: 2012-08-20
forum: General Help
---

### Post by DavinciiG on 2012-08-20
Hi, Im quite new to Ubuntu and im trying to install several 32 bits applications like adoberead, skype and others but i having trouble with the libraries. 

i know that ia32-libs is a temporary hack and is fading away but even if i use 
```
sudo apt-get install package-name:i386
```I'm not able to install this programs there is always a problem with a dependency so i don't know what to do can any one help

here is an example of what happen when i try to install adoberead 

```
david@Workstation:~$ sudo apt-get install adobereader:i386

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 acroread:i386 : Depends: libgdk-pixbuf2.0-0:i386 (>= 2.22.0) but it is not going to be installed
                 Depends: libgtk2.0-0:i386 (>= 2.24.0) but it is not going to be installed
                 Depends: libpango1.0-0:i386 (>= 1.14.0) but it is not going to be installed
                 Depends: libx11-6:i386 but it is not going to be installed
                 Depends: libxext6:i386 but it is not going to be installed
                 Depends: libxt6:i386 but it is not going to be installed
                 Depends: acroread-common:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.
```Thx in advance

---

### Post by Bucky Ball on 2012-08-20
Welcome.

Skype is in the repositories. Install with Software Centre or Synaptics.

Think Adoberead is in there also. (Document Viewer should be installed by default, though, unless you have a special reason for using Adobe Read. Try opening a PDF and see what you get now.) You could also install ubuntu-restricted-extras for a heap of codecs and other bits and pieces. 

Make sure you have the partner repositories enabled by going to Software Sources (Update Manager then hit 'Settings' in the bottom left hand corner) and go to the 'Other Software' tab. Make sure 'Canonical Partners' and 'Independent' are ticked.

Always check the repos for the app first or see if you can add a repo for that app. That way it will get updated automatically which won't happen when you install manually (unless you do it yourself).

---

### Post by DavinciiG on 2012-08-20
Hey thx for your quick answer, i already try to intalling the programs using Software Centre or Synaptics but still i have the same problem it tell me that the Package dependencies cannot be resolved.
any other ideas?

---

### Post by Bucky Ball on 2012-08-20
Yep, try installing ubuntu-restricted-extras and then try again. Skype probably needs third-party codecs or some such which you currently don't have installed.

Weird that the version in the repos is missing dependencies, though. That shouldn't be. Have you uninstalled anything major lately (or minor)? This may fix things. Run these two commands in a terminal:

sudo apt-get update
sudo apt-get upgrade

That will fix some things it looks like you have held back. The upgrade upgrades packages and dependencies, NOT the release (to 12.10 for instance). Try that first but **always** run the update command first. :)

---

### Post by DavinciiG on 2012-08-22
Ok  i already had install the ubuntu-restricted-extras before so that is not.
Now i did what you told me and when i run 
```
sudo apt-get update
```i get this message at the end
```
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```So i run  apt-get update again but it keeps giving me the same message any way after i did the  apt-get upgrade and upgraded some packages then i try to install adobe read
by the software center and again the same error
**Package dependencies cannot be resolved**
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
```
acroread:i386: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
               Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed

```and using the  apt-get install i get the same error as before. and for all the i382 applications i have the same problem
I have try to install the ia32-libs and then reinstall multiarch but no luck plz help
I don't know what to do

---

### Post by Bucky Ball on 2012-08-22
Okay, could you open a terminal and issue:

```
gedit /etc/apt/sources.list
```

Copy and paste that file back here, between code tags, please. ;)

---

### Post by DavinciiG on 2012-08-22
here it is 
```

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ precise universe
deb http://fr.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner
```

---

### Post by DavinciiG on 2012-08-23
[LEFT]Ok i finally fix it with synaptic. The problem was that the package Xlib6:i386 that i had download was corrupted so i could not install ia32-lib-multiarch.

Download new package and run synaptic and fix I'm now able to install the i386 applications. 
tho im still getting 
```
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```when i do```
 apt-get update 
```some one nows how can i fix this?


aaaa and thx Bucky Ball for your help


[/LEFT]

---

### Post by mungatsuma on 2012-11-14
For the duplicate sources list, try using [chkdup]("http://http://askubuntu.com/questions/30585/how-can-i-automatically-remove-duplicate-sources-list-entries") from the link. I have used it several times and it works.

---

