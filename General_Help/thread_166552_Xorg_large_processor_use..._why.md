---
title: "Xorg large processor use... why??"
date: 2006-04-26
forum: General Help
---

### Post by jms830 on 2006-04-26
Xorg periodically jumps and uses alot of my processor, why is this? Right now it isn't freezing my computer completely, but it often does. Below is the results of top.  One hypothesis I've had is that I'm using the latest NVidia drivers and that might cause a problem?

top - 16:26:46 up 13:53,  2 users,  load average: 0.86, 0.98, 0.88
Tasks: 101 total,   2 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s): 96.3% us,  3.3% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.4% si
Mem:   1035992k total,  1005848k used,    30144k free,    91272k buffers
Swap:  1004052k total,        0k used,  1004052k free,   471660k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8474 root      25   0  187m  64m  13m R 80.0  6.4  32:04.39 Xorg
 9720 jordan    15   0 62264  35m  10m S  7.7  3.5  29:44.50 nicotine
 9660 jordan    15   0 31920  14m 9788 S  5.9  1.5   0:23.42 gnome-terminal
 9611 jordan    15   0 54096  26m  13m S  3.3  2.6   2:34.17 gaim
 8377 hal       17   0  1868  760  660 S  0.4  0.1   4:48.16 hald-addon-stor
 9490 jordan    16   0 17436 9148 6620 S  0.4  0.9   0:00.77 gnome-session
 9601 jordan    15   0 68720  65m  708 S  0.4  6.5   0:32.69 xcompmgr
 9718 jordan    16   0 14060 6032 4680 S  0.4  0.6   0:00.78 alltray
 9833 jordan    16   0  109m  30m  18m S  0.4  3.1   0:06.99 mozilla-thunder
22219 jordan    15   0  114m  43m  15m S  0.4  4.3   0:40.08 firefox-bin
    1 root      16   0  1556  524  456 S  0.0  0.1   0:01.34 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.29 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.13 events/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   67 root      10  -5     0    0    0 S  0.0  0.0   0:00.17 kblockd/0

---

### Post by s.toonen on 2008-05-01
My guess is that it is due to alltray. I had the same problem while keeping my gnome-terminal opened with alltray. Try killing it and if the cpu usage of xorg drops significant, you know the source.

---

