---
title: "Ubuntu locking up minutes after boot"
date: 2011-12-21
forum: General Help
---

### Post by MentalTeryn on 2011-12-21
First let me begin by saying I'm new to Linux and this is my first post to these forums.

Anyways, I wanted to learn Linux and I felt the best way to learn was to dive head first. Everything went fine with my initial installation and had no problems logging in for the first time. I ran the first barrage of updates and shut down my laptop for the night. Now however, Ubuntu is locking up consistently ~5 minutes after booting up. After several attempts i found that it locks up moments after apt-check appears in the process list. After which I'm unable to do anything. Mouse is unresponsive, windows can't be moved, alt-tab doesn't do anything, etc. I'm only able to break free using REISUB. Any help would be greatly appreciated. :)

---

### Post by MentalTeryn on 2011-12-21
Here's a quick look at what TOP said before the most recent lockup:

PID    User      PR   NI  VIRT  RES    SHR   S  %cpu  %mem   TIME+    command
1858  corey     20    0  269m  9.9m  7524  S     1         0.2     0:00.04   update-notifier
1863  corey     39  19  80148  16m   3668  R     1         0.4    0:00.03   apt-check
897 messageb 20    0  25184  2160  1080  S     1         0.1    0:00.41   dbus-daemon
1438  corey     20    0  26908  2664   864   S    1         0.1    0:00.83   dbus-daemon
1547  corey     20    0  626m  183m  41m  S     1         4.6     0:02.16  compiz
1175  root       20    0  157m   33m   15m  S     0         0.8     0:01.87  Xorg
1853  corey     20    0  21460  1368   992  R     0         0.0     0:00.06  Top 
   1    root        20   0  24168   2204  1324 S     0         0.1     0:00.50  init

Hopefully this'll help.

---

