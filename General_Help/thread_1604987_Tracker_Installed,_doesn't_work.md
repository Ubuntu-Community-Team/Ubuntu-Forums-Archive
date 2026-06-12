---
title: "Tracker Installed, doesn't work?"
date: 2010-10-24
forum: General Help
---

### Post by Daemn on 2010-10-24
I have tracker, tracker-utils, tracker-search-tool, and tracker-gui installed.

I can run tracker-preferences and see that it's enabled and has my home directories added.

I can run tracker-search-tool and type something into the search box, hit enter, and it does nothing.

I can run tracker-tags -t and it shows all the files I've tagged via right-click -> properties -> tags (nautilus python extension) in shell.

The only 'tracker' process I see running is 'tracker-store' not trackerd or tracker-indexer.

Can anyone point me the right direction please?

---

### Post by calimerox on 2010-10-28
same happens to me,

it says that files were found when you go for a search but you just cant see the files ....edit note: i just installed beagle and on first spot it looks more straight forward that tracker-search-tool...

---

### Post by Ronok on 2011-01-02
RE: **tracker-store**

on a clients computer 
that they were complaining was slow
I found using:
(Applications > Accessories > Terminal)

```
user@computer:~$ **top**

PID USER      PR  NI  VIRT  RES  SHR S **%CPU** %MEM    TIME+  COMMAND
 3062 root       20   0  309m 130m  86m R   77 13.1   2:03.03 tracker-store                                           
 1664 user       20   0 19332  11m 3408 R   32  1.1   9:54.37 tracker-store                                          
 1648 user       39  19 35392 5576 2872 S    0  0.5   0:15.13 tracker-miner-f                                         
 1652 user       20   0 36012 7240 6528 S    0  0.7   0:01.01 tracker-status- 
```

it was making that machine Catatonic
so
System > Administration > Synaptic Package Manager >
quick search: tracker
right click > Mark for Complete Removal

Version# was:
0.8.17-0ubuntu1 (tracker-gui)
Kernel		: Linux 2.6.35-24-generic (i686)
Distribution		: Ubuntu 10.10


Now everything is smooth again!
[URL="http://www.gongkuo.com/linuxcli.htm"]Ronok
[SIZE="1"]My < Linux > Command Line Interface Page[/SIZE][/URL]

---

### Post by AlwaysLearning on 2011-02-01
Grep your /var/log/kern.log and /var/log/syslog files for tracker. If you can see entries like these:
```
kern.log:Jan 21 09:31:56 router kernel: [ 3623.429775] tracker-indexer[1935]: segfault at 0 ip 001dc8f9 sp bfcccdf0 error 4 in libsqlite3.so.0.8.6[18a000+80000]
syslog:Jan 21 09:31:56 router kernel: [ 3623.429775] tracker-indexer[1935]: segfault at 0 ip 001dc8f9 sp bfcccdf0 error 4 in libsqlite3.so.0.8.6[18a000+80000]
```
... then your tracker search catalogs are probably broken. You can reset them again with the following commands:
```
# Stops tracker processes and resets search databases
tracker-control -r
# Restarts tracker and miner processes
tracker-control -s
# Restarts the gnome panel icon
tracker-status-icon
```

Good luck,
AL.

---

