---
title: "splashy installation problem..."
date: 2009-08-18
forum: General Help
---

### Post by tanixmukherzee on 2009-08-18
i am having a problem installing splashy in ubuntu jaunty...
the console is showing something like...

[COLOR="Sienna"]tanixmukherzee@tanbuntu:~$ sudo apt-get install splashy
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Suggested packages:
splashy-themes console-common
The following NEW packages will be installed:
splashy
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1180kB of archives.
After this operation, 1831kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe splashy 0.3.13-3ubuntu1 [1180kB]
Fetched 1180kB in 37s (31.1kB/s) 
(Reading database ... 216261 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-3ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb (--unpack):
trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base
Processing triggers for man-db ...
Errors were encountered while processing
/var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

i am seeing this error...what to do...
i was getting some problem to activate usplash screen in ubuntu jaunty...so i tried to install splashy removing usplash
any ideas?

---

### Post by jwaffolter on 2009-08-18
I received the same error too..
I was able to remedy it by adding the following line to /etc/apt/sources.list
deb[COLOR=Black] [http://ppa.launchpad.net/tohms/bugfixes/ubuntu](http://ppa.launchpad.net/tohms/bugfixes/ubuntu)[/COLOR] jaunty main

afterwards run sudo apt-get update(don't worry about any gpg errors)
and try installing splashy afterwards

hth

edit: Official bug report- [https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089](https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089)

---

### Post by tanixmukherzee on 2009-08-18
thanks bro...seems it works!:KS

---

### Post by jwaffolter on 2009-08-18
glad I could help :)

---

### Post by cthlhu1987 on 2009-10-06
Holy $%&#, it worked!!! Thx a lot :KS:popcorn::D:guitar::cool:

---

