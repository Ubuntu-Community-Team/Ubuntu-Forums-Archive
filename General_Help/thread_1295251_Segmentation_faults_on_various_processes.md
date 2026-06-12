---
title: "Segmentation faults on various processes"
date: 2009-10-19
forum: General Help
---

### Post by smartt on 2009-10-19
hi guys,

after i could not reach my machine some days ago, i started a remote reset through my hosters interface for that. Now i have problems. I get strange segfaults with many processes, f.e.:

```

root@mymachine:~# aptitude update
Segmentation fault
root@mymachine:~# aptitude update
Segmentation fault
root@mymachine:~# aptitude update
Get:1 ftp://mirror.hetzner.de jaunty Release.gpg [189B]
Get:2 ftp://mirror.hetzner.de jaunty/main Translation-en_US
Ign ftp://mirror.hetzner.de jaunty/main Translation-en_US
Get:3 ftp://mirror.hetzner.de jaunty/restricted Translation-en_US
Ign ftp://mirror.hetzner.de jaunty/restricted Translation-en_US
Get:4 http://de.archive.ubuntu.com jaunty Release.gpg [189B]
Get:5 http://de.archive.ubuntu.com jaunty-updates Release.gpg [189B]
Get:6 ftp://mirror.hetzner.de jaunty/universe Translation-en_US
Ign ftp://mirror.hetzner.de jaunty/universe Translation-en_US
......................

```2 segfaults, 3rd time it worked

```

apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  graphicsmagick libgraphicsmagick1 libsndfile1 python-zopeinterface tzdata tzdata-java
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3335kB of archives.
After this operation, 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 ftp://mirror.hetzner.de jaunty-updates/main tzdata-java 2009n-0ubuntu0.9.04.1 [141kB]
Get:2 ftp://mirror.hetzner.de jaunty-updates/main tzdata 2009n-0ubuntu0.9.04.1 [691kB]
Get:3 ftp://mirror.hetzner.de jaunty-updates/universe libgraphicsmagick1 1.1.11-3.2+lenny1build0.9.04.1 [1213kB]
Get:4 ftp://mirror.hetzner.de jaunty-updates/universe graphicsmagick 1.1.11-3.2+lenny1build0.9.04.1 [946kB]
Get:5 ftp://mirror.hetzner.de jaunty-updates/main libsndfile1 1.0.17-4ubuntu1.1 [198kB]
Get:6 ftp://mirror.hetzner.de jaunty-updates/main python-zopeinterface 3.4.0-0ubuntu3.3 [146kB]
Fetched 3335kB in 0s (6399kB/s)
Preconfiguring packages ...
Can't use an undefined value as an ARRAY reference at /usr/share/perl5/Debconf/ConfModule.pm line 321, <GEN1> line 9.
/bin/sh: line 1: 18982 Segmentation fault      /usr/sbin/dpkg-preconfigure --apt
(Reading database ... 49081 files and directories currently installed.)
Preparing to replace tzdata-java 2009n-0ubuntu0.9.04 (using .../tzdata-java_2009n-0ubuntu0.9.04.1_all.deb) ...
Unpacking replacement tzdata-java ...
E: Sub-process /usr/bin/dpkg received a segmentation fault.

```again segfaults....

with apt i get 

```

Could not execute '/usr/bil/gpgv' to verify signature (is gpgv installed?)
```right.../usr/bil/ !? What is that? I checked my syslog and various other processes are not working (cron etc.). Could that be a hardware issue or what do you think?
Please help me...


regards, Thomas

---

### Post by Giblet5 on 2009-10-19
This system has a corrupted OS or the hardware is failing.

Probably not what you want to hear...

Reboot, run memtest86 for two hours. Fix anything wrong with the hardware. Then boot in Recovery mode, run fsck and try to clean up the root fs.

---

### Post by smartt on 2009-10-19
thanks for your response. Yes, it was the ram. Hoster changed it, now it works again.

---

