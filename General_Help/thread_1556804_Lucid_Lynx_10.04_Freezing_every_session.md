---
title: "Lucid Lynx 10.04 Freezing every session"
date: 2010-08-19
forum: General Help
---

### Post by ddotspot on 2010-08-19
I've had this distro for a couple months, now it has begun freezing at random on me. The mouse continues to move, but only a hard reset will free it up. I booted into failsafe and didn't have it freeze on me, but I was just reading these forums.  I posted htop results, not sure if that will help anything. Can anyone lend a hand?


  CPU[||||||||||||||||||||||||100.0%]     Tasks: 217 total, 2 running
  Mem[||||||||||||||||||||317/1002MB]     Load average: 2.18 1.57 1.41 
  Swp[                      0/1650MB]     Uptime: 01:03:25

  PID   USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 1677     root      20   0  8184  4412  2064 R 90.0  0.4 41:47.52 /usr/bin/python /u
 2174    daniel    20   0  327M 75084 30520 S  3.0  7.3  2:46.06 /usr/lib/firefox-3
 2884    daniel    20   0  2580  1244   960 R  2.0  0.1  0:01.00 htop
 894      root      20   0 81568 64520 11552 S  1.0  6.3  1:58.25 /usr/bin/X :0 -nr
 2526    daniel    20   0  172M 44548 20084 S  1.0  4.3  0:11.71 /usr/bin/skype
 2782    daniel    20   0 45828 13088  9972 S  1.0  1.3  0:01.33 gnome-terminal
 1594    daniel    20   0 36692 12292  9652 S  0.0  1.2  0:04.92 metacity
 1598    daniel    20   0 43176 16276 11324 S  0.0  1.6  0:05.55 gnome-panel
 1630    daniel    20   0 39832 13512 10420 S  0.0  1.3  0:04.29 /usr/lib/gnome-pan
 2179    daniel    20   0  327M 75084 30520 S  0.0  7.3  0:03.89 /usr/lib/firefox-3
 1482    root      20   0  3604  1192  1016 S  0.0  0.1  0:00.18 hald-addon-storage
 1458    root      20   0  3600  1200  1024 S  0.0  0.1  0:02.59 hald-addon-input:
 1583   daniel    20   0 89712  9988  7288 S  0.0  1.0  0:02.57 /usr/lib/gnome-set
 1612    root      20   0  5172   948   672 S  0.0  0.1  0:01.45 udisks-daemon: pol
 2672    root      20   0 55124 45960  7692 S  0.0  4.5  0:07.13 /usr/bin/X :1 -br
 1479    root      20   0  3604  1192  1016 S  0.0  0.1  0:00.88 hald-addon-storage
    1      root      20   0  2800  1648  1180 S  0.0  0.2  0:00.45 /sbin/init
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

---

