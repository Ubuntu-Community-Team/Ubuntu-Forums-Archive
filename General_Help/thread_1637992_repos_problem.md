---
title: "repos problem"
date: 2010-12-05
forum: General Help
---

### Post by joe iwannou on 2010-12-05
[IMG]http://img15.imageshack.us/img15/4554/diaxeirhsherror.png[/IMG]
im from greece and i have repos problem 
that message says in folder /etc/apt/sources.list.d/xorg-edgers-
-ppa-lucid.list has in secont line an "n" and that makes all
problems to me  
i cant make update and if anyone knows how to remove than "n"
lets do it
thanks

---

### Post by overdrank on 2010-12-05
Hi and this [RepositoriesCommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine") should help with editing the source list on your system. :)

---

### Post by joe iwannou on 2010-12-05
> **overdrank said:**
> Hi and this [RepositoriesCommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine") should help with editing the source list on your system. :)

thaks anyway but my english is bad

---

### Post by overdrank on 2010-12-05
> **joe iwannou said:**
> thaks anyway but my english is bad

Ok sorry. I will try and help. Can you post the output of this command in the terminal.
```
cat /etc/apt/sources.list

```
Edit you may find help here easier :)
[http://forum.ubuntu-gr.org/](http://forum.ubuntu-gr.org/)

---

### Post by joe iwannou on 2010-12-05
> **overdrank said:**
> Ok sorry. I will try and help. Can you post the output of this command in the terminal.
```
cat /etc/apt/sources.list

```
Edit you may find help here easier :)
[http://forum.ubuntu-gr.org/](http://forum.ubuntu-gr.org/)

```
joe@joe-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gr.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gr.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://dl.google.com/linux/deb/ testing non-free
```

how can edit source.list?

---

