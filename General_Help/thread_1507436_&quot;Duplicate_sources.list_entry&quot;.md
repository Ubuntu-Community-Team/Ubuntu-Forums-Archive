---
title: "&quot;Duplicate sources.list entry&quot;"
date: 2010-06-11
forum: General Help
---

### Post by jrg3 on 2010-06-11
When I do sudo apt-get update I'm forced to do it twice because after the first run I receive this output:

```
Fetched 170kB in 1s (96.8kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

I've edited sources.list many times trying to resolve this with no luck. 

I figure you'll need to see my sources.list:


```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse main universe restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

## jrg3 added
# Chromium Daily Builds | jrg3
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
deb http://archive.canonical.com/ lucid partner

# Google software repository | jrg3
deb http://dl.google.com/linux/deb stable non-free main

# Moblock software repository | jrg3
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main

# Virtualbox software repository | jrg3
deb http://download.virtualbox.org/virtualbox/debian lucid non-free

```

---

### Post by JohnnyC35 on 2010-06-11
ya I hate it when my source list gets duplicates and you have to track them down. if apt finds duplicates it should auto-remove them.

---

### Post by plucky on 2010-06-11
```
# Chromium Daily Builds | jrg3
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
[color=red]deb http://archive.canonical.com/ lucid partner[/color]

```

The line in red is a duplicate of the same line further up the list.
Remove it and run the update again.

Good Luck

---

### Post by IvoriesAblaze on 2010-06-22
> **plucky said:**
> ```
# Chromium Daily Builds | jrg3
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
[color=red]deb http://archive.canonical.com/ lucid partner[/color]

```

The line in red is a duplicate of the same line further up the list.
Remove it and run the update again.

Good Luck
Worked like a charm. Thanks!

---

### Post by potatochip on 2011-09-24
Use this to find duplicate lines;

grep -v ^# /etc/apt/sources.list | sort | uniq -c | sort

---

### Post by Slezhuk on 2011-11-18
In my case there was entry in /etc/apt/**sources.list.d**/lucid-partner.list

---

### Post by Bucic on 2011-12-16
I don't see any duplicates in my sources. Could anyone point them out for me, please?
```

**grep -v ^# /etc/apt/sources.list | sort | uniq -c | sort**
      1 deb http://archive.canonical.com/ubuntu oneiric partner
      1 deb http://extras.ubuntu.com/ubuntu oneiric main
      1 deb http://ftp.vectranet.pl/ubuntu/ oneiric-backports main restricted universe multiverse
      1 deb http://ftp.vectranet.pl/ubuntu/ oneiric main restricted universe multiverse
      1 deb http://ftp.vectranet.pl/ubuntu/ oneiric-security main restricted universe multiverse
      1 deb http://ftp.vectranet.pl/ubuntu/ oneiric-updates main restricted universe multiverse
      1 deb-src http://archive.canonical.com/ubuntu oneiric partner
      1 deb-src http://extras.ubuntu.com/ubuntu oneiric main
      1 deb-src http://ftp.vectranet.pl/ubuntu/ oneiric-backports main restricted universe multiverse #Added by software-properties
      1 deb-src http://ftp.vectranet.pl/ubuntu/ oneiric restricted main multiverse universe #Added by software-properties
      1 deb-src http://ftp.vectranet.pl/ubuntu/ oneiric-security main restricted universe multiverse #Added by software-properties
      1 deb-src http://ftp.vectranet.pl/ubuntu/ oneiric-updates main restricted universe multiverse #Added by software-properties


```
"cleaner" form:
```

http://archive.canonical.com/ubuntu oneiric partner
http://archive.canonical.com/ubuntu oneiric partner
http://extras.ubuntu.com/ubuntu oneiric main
http://extras.ubuntu.com/ubuntu oneiric main
http://ftp.vectranet.pl/ubuntu/ oneiric main restricted universe multiverse
http://ftp.vectranet.pl/ubuntu/ oneiric restricted main multiverse universe #Added by software-properties
http://ftp.vectranet.pl/ubuntu/ oneiric-backports main restricted universe multiverse
http://ftp.vectranet.pl/ubuntu/ oneiric-backports main restricted universe multiverse #Added by software-properties
http://ftp.vectranet.pl/ubuntu/ oneiric-security main restricted universe multiverse
http://ftp.vectranet.pl/ubuntu/ oneiric-security main restricted universe multiverse #Added by software-properties
http://ftp.vectranet.pl/ubuntu/ oneiric-updates main restricted universe multiverse
http://ftp.vectranet.pl/ubuntu/ oneiric-updates main restricted universe multiverse #Added by software-properties

```

BTW, thanks for the tip, **potatochip**!

---

