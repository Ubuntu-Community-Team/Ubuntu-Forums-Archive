---
title: "Authentication Failure"
date: 2011-05-20
forum: General Help
---

### Post by FinalShot on 2011-05-20
Whenever I try to install any program via the Software Centre I get "Auth Failure", I'm unsure what could have caused this unfortunately.

Any help is appreciated.

---

### Post by zvacet on 2011-05-20
```
cat /etc/apt/sources.list
```

post it here.Do you get any errors when you try 

```
sudo apt-get update && sudo apt-get upgrade
```

if you do please post them too.

---

### Post by linuxinstalledfromhdd on 2011-05-20
sudo synaptic

What error message to you get?

---

### Post by FinalShot on 2011-05-20
```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.optus.net/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.optus.net/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.optus.net/ubuntu/ lucid universe
deb http://mirror.optus.net/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.optus.net/ubuntu/ lucid multiverse
deb http://mirror.optus.net/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://mirror.optus.net/ubuntu/ lucid-security main restricted
deb http://mirror.optus.net/ubuntu/ lucid-security universe
deb http://mirror.optus.net/ubuntu/ lucid-security multiverse
deb http://ppa.launchpad.net/cdemu/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/cdemu/ppa/ubuntu lucid main
```Errors from apt-get.
```
W: Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

When I run *sudo synaptic* Synaptic opens fine.

---

### Post by FinalShot on 2011-05-22
Bump.

---

### Post by FinalShot on 2011-05-22
Whenever I try installing a program via the Software Centre, I get Authentication failure. However, if I run:

```
gksu /usr/bin/software-center
```

I can install things fine. When I first installed 10.04, I would have been asked to enter my password, how can I revert it back?

---

### Post by linuxinstalledfromhdd on 2011-05-22
try a clean reinstallation of software-center

---

### Post by FinalShot on 2011-05-22
This happens with all programs (ex: Disk Utility ).

---

### Post by FinalShot on 2011-05-23
Bump.

---

### Post by FinalShot on 2011-05-24
Bump.

---

### Post by zvacet on 2011-05-24
In terminal 

```
gksudo gedit /etc/apt/sources.list
```

and remove lines with PPA repository.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by FinalShot on 2011-05-24
I removed these lines from /etc/apt/sources.list ( probably removed wrong ones ):
```
deb http://ppa.launchpad.net/cdemu/ppa/ubuntu lucid main deb-src
http://ppa.launchpad.net/cdemu/ppa/ubuntu lucid main
```Running *sudo apt-get update && sudo apt-get upgrade* spits out:
```
W: Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```No offense, but how does this help solve my authentication problem?

---

### Post by wildmanne39 on 2011-05-24
> **FinalShot said:**
> I removed these lines from /etc/apt/sources.list ( probably removed wrong ones ):
```
deb http://ppa.launchpad.net/cdemu/ppa/ubuntu lucid main deb-src
http://ppa.launchpad.net/cdemu/ppa/ubuntu lucid main
```Running *sudo apt-get update && sudo apt-get upgrade* spits out:
```
W: Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```No offense, but how does this help solve my authentication problem?
Hi, the one with the vlc also needs to be remove and then your updates should work correctly, if not run these commands.
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by FinalShot on 2011-05-24
The VLC one isn't in /etc/apt/sources.list, I run those commands but they appeared to make no difference.

And again, how does fixing this help my authentication problem?

---

### Post by oldos2er on 2011-05-24
Look in /etc/apt/sources.list.d/ for a *.list and *.list.save file with c-korn in its name. Delete them (you'll need admin privileges to do this) and run **sudo apt-get update.**

---

### Post by FinalShot on 2011-05-25
Well, sudo apt-get update no longer spits out any errors. **But how does this help solve my authentication problem?**

---

### Post by oldos2er on 2011-05-26
You removed the repository that was having authentication problems.

---

### Post by FinalShot on 2011-05-26
Well I still get Auth Failure when trying to install an application from the software centre, or even trying to delete a partition in disk utility.

---

### Post by oldos2er on 2011-05-27
> **FinalShot said:**
>  even trying to delete a partition in disk utility.

That's a very different problem. Do you have 'sudo' or admin privileges on the system in question? Can you provide a screenshot of the error?

---

### Post by LordNeo on 2011-05-27
have you tried to just change your password and check if it happens?

do it from gui or from terminal (passwd)

also do dpkg-reconfigure -a

---

### Post by FinalShot on 2011-05-28
Yes I have sudo privileges. First [this]("http://img705.imageshack.us/img705/5769/screenshot1dw.png") flashes around, then [this]("http://img23.imageshack.us/img23/5437/screenshotzd.png") pops up.

And changing my password didn't help.

---

### Post by FinalShot on 2011-05-29
Bump.

---

### Post by oldos2er on 2011-05-29
If you run ```
gksu gnome-disk-utility
``` do you get the same errors?

---

### Post by FinalShot on 2011-05-29
When I run:
```
gksu gnome-disk-utility
```It asks me to input my password, but it never starts.

However, if I run:
```
gksu palimpsest
```It opens, and I can delete & creation partitions fine. The problem is, I want to be asked my password when creating & deleting partitions, not starting every program with gksu. And when I installed ubuntu, I would have been asked my password before performing administrative actions.

---

### Post by FinalShot on 2011-05-31
Bump.

---

### Post by FinalShot on 2011-06-01
Bump.

---

### Post by FinalShot on 2011-06-03
Bump.

---

