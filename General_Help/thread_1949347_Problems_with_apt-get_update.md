---
title: "Problems with apt-get update"
date: 2012-03-30
forum: General Help
---

### Post by viktorjano on 2012-03-30
Hi!

When trying to update apt-get this massage appears

```
sskt-linux@ssktlinux:~$ sudo apt-get update
[sudo] password for sskt-linux: 
E: The method driver /usr/lib/apt/methods/http// could not be found.
sskt-linux@ssktlinux:~$ 
```Prior to that I added some repositories... and after adding those repositories this problem occurred...

---

### Post by codemaniac on 2012-03-30
try installing the package .
```
sudo apt-get install apt-transport-https
```

---

### Post by viktorjano on 2012-03-30
Hey, codemaniac

seems that I have allready installed on my Ubuntu...

```
sskt-linux@ssktlinux:~$ sudo apt-get install apt-transport-https
[sudo] password for sskt-linux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apt-transport-https is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-12 linux-headers-3.0.0-12-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sskt-linux@ssktlinux:~$ 
```What would I do next?



> **codemaniac said:**
> try installing the package .
```
sudo apt-get install apt-transport-https
```

---

### Post by codemaniac on 2012-03-30
Can you post your sources.list file , so that we can track out what is wrong with your repository list ?

---

### Post by viktorjano on 2012-03-30
Here is the source.list file

```
# deb cdrom:[Edubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mk.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://mk.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://mk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mk.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://mk.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://mk.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://mk.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mk.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://mk.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://mk.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://mk.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mk.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://mk.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http//:archive.canonical.com/ oneiric partner
deb-src http//:archive.canonical.com/ oneiric partner
```

---

### Post by Adrian98 on 2012-03-30
I was having same error message and I tried to install the package and It fixed it!! Thanks you all people!!

---

### Post by viktorjano on 2012-03-30
Hey!

I edited the source.list file. Actually, I manually deleted the last repositories that I added and after that the apt-get update went well!!!

Thanks codemanic!!!

---

### Post by codemaniac on 2012-03-30
> **viktorjano said:**
> Hey!

I edited the source.list file. Actually, I manually deleted the last repositories that I added and after that the apt-get update went well!!!

Thanks codemanic!!!

Actually your last two urls were seemed suspicious , specially the ":" before url .

```
deb http//:archive.canonical.com/ oneiric partner
deb-src http//:archive.canonical.com/ oneiric partner
```

---

