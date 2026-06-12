---
title: "Repository problem?"
date: 2009-10-01
forum: General Help
---

### Post by Calixte on 2009-10-01
Can't install anything (via repositories) nor update

I get this error message when I try to update my system or add software using apt-get or the add/remove thingy:
```

The repository may no longer be available or could not be contacted because of
network problems. If available an older version of the failed index will be used.
Otherwise the repository will be ignored. Check your network connection and ensure the
repository address in the preferences is correct.
```
then:
```
E: Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)
E: Unable to lock the list directory

```

I tried this:
```
Xxxx@Yyyy:~$ sudo apt-get clean && sudo mv /var/lib/apt/lists
/var/lib/apt/lists.old && sudo mkdir
-p /var/lib/apt/lists/partial && sudo apt-get clean && sudo apt-get update
[sudo] password for Xxxx:
E: Lists directory /var/lib/apt/lists/partial is missing.
```

But I still got an error.

Any ideas?

Thanks in advance!

PS: I already tried to change my server to the main one.

---

### Post by Woody1987 on 2009-10-01
What version of ubuntu are you using?

can you copy the output of cat /etc/apt/sources.list

---

### Post by Calixte on 2009-10-01
9.04

actually, Easy Peazy, because NBR did not detect my hardware properly :S

```
calixte@Lucy:~$ cat /etc/apt/sources.list 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Easy Peasy security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Easy Peasy 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Easy Peasy security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Easy Peasy users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe

```

---

