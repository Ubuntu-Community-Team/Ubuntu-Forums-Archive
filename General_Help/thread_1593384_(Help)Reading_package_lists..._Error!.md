---
title: "(Help)Reading package lists... Error!"
date: 2010-10-11
forum: General Help
---

### Post by b4tt054y on 2010-10-11
Help me for solve this problem my pc: 
```
 Hit http://id.archive.ubuntu.com lucid-backports/main Packages
Hit http://id.archive.ubuntu.com lucid-backports/restricted Packages
Hit http://id.archive.ubuntu.com lucid-backports/universe Packages
Hit http://id.archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://id.archive.ubuntu.com lucid-backports/main Sources
Hit http://id.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://id.archive.ubuntu.com lucid-backports/universe Sources
Hit http://id.archive.ubuntu.com lucid-backports/multiverse Sources
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing libmpeg4ip-0 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.offensive-security.com_dists_pwnsauce_multiverse_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.
root@r00t-hunt3r:~# 

```i just one to solve this problem. PLease :) :P



I'm new in here by the way. Im from indonesian. Greetings ! :)

---

### Post by b4tt054y on 2010-10-13
Helppppp pleaseeeeeee!!

---

### Post by CompyTheInsane on 2010-10-13
Can you post the contents of /etc/apt/sources.list?

---

### Post by emoguitarist06 on 2010-10-13
It seems that your problem was Solved in this thread
[http://ubuntuforums.org/showthread.php?t=1570277]("http://ubuntuforums.org/showthread.php?t=1570277")

---

### Post by b4tt054y on 2010-10-14
> **compugeek32 said:**
> Can you post the contents of /etc/apt/sources.list?



This is my list 
```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid$
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://id.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://id.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://id.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://id.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://id.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://id.archive.ubuntu.com/ubuntu/ lucid universe
deb http://id.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://id.archive.ubuntu.com/ubuntu/ lucid-updates universe
# N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://id.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://id.archive.ubuntu.com/ubuntu/ lucid universe
deb http://id.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://id.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://id.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://id.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://id.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://id.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://id.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://id.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

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
deb http://archive.offensive-security.com pwnsauce main microverse macroverse restricted universe multiverse


 lines to add software from the 'backports'
## repository.



```

---

