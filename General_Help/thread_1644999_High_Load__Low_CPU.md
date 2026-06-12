---
title: "High Load | Low CPU"
date: 2010-12-14
forum: General Help
---

### Post by domzz on 2010-12-14
I need some help, **Im a noob**.
I get high load, but low CPU. I am not sure what to do
Here is my Top. 

> top - 07:40:18 up 17 days,  9:08,  2 users,  load average: 6.44, 6.31, 6.44
Tasks: 315 total,   2 running, 296 sleeping,  17 stopped,   0 zombie
Cpu(s):  0.3%us,  0.6%sy,  0.0%ni, 86.9%id, 11.8%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:  12316104k total, 12243856k used,    72248k free,    17216k buffers
Swap:  1052472k total,        0k used,  1052472k free, 11433024k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4354 xxxx  20   0  171m  55m  45m D    2  0.5   6:44.44 rtorrent
24259 xxxx2   20   0  681m 321m 305m D    1  2.7   0:10.49 rtorrent
10699 xxxx3  20   0  297m  37m  14m D    1  0.3  11:50.12 rtorrent
16737 root      20   0     0    0    0 D    1  0.0  17:28.64 flush-9:2
  611 root      20   0     0    0    0 S    0  0.0  74:05.18 kswapd0
 1657 root      20   0     0    0    0 S    0  0.0   4:04.33 kondemand/5
 1658 root      20   0     0    0    0 R    0  0.0   1:43.66 kondemand/6
 1852 root      20   0     0    0    0 S    0  0.0  55:59.89 md2_raid1
 3303 root      20   0     0    0    0 S    0  0.0  60:53.45 jbd2/md2-8
 4793 xxxx4  20   0  226m  31m  22m S    0  0.3   3:08.48 rtorrent
 5980 xxxx4  20   0 98.8m  15m 4384 S    0  0.1  64:52.84 rtorrent
23145 xxxx4  20   0 41240 1788 1116 S    0  0.0   0:00.52 pure-ftpd
23372 xxxx5   20   0  141m  27m  14m S    0  0.2  18:54.53 rtorrent
24606 root      20   0 19404 1496  960 R    0  0.0   0:00.04 top
    1 root      20   0 23744 1476  888 S    0  0.0   0:08.05 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd


Also When I run
# top -b -n 1 | awk '{if (NR <=7) print; else if ($8 == "D") {print; count++} } END {print "Total status D: "count}'

>  4550 xxxx  20   0 41240 1796 1124 D    2  0.0   0:45.05 pure-ftpd
10699 xxxx1      20   0  321m  37m  13m D    2  0.3  11:50.70 rtorrent
24259 xxxx2      20   0  535m 206m 190m D    2  1.7   0:14.78 rtorrent
 3303 root      20   0     0    0    0 D    0  0.0  60:53.86 jbd2/md2-8
 4793 xxxx3  20   0  226m  33m  24m D    0  0.3   3:09.29 rtorrent
14994 root      20   0     0    0    0 D    0  0.0  12:18.82 md2_resync
16737 root      20   0     0    0    0 D    0  0.0  17:29.19 flush-9:2
23372 xxxx4    20   0  143m  27m  14m D    0  0.2  18:54.83 rtorrent   

When I type: 

#free -m
>              total       used       free     shared    buffers     cached
Mem:         12027      11957         70          0         16      11164
-/+ buffers/cache:        775      11251
Swap:         1027          0       1027   

---

### Post by amauk on 2010-12-14
12% of the CPU time is spent on waiting for disk I/O to complete
You've also got 6 rtorrent processes running

The high load is most likely because your disks are being hammered with lots of reads/writes from rtorrent, and this is causing other processes to be delayed

Try stopping rtorrent and seeing if the load reduces
If it does, then either throttle back rtorrent so it doesn't access your disk so often, or get faster disks

---

### Post by domzz on 2010-12-14
I have set 
send_buffer_size = 2M
receive_buffer_size = 2M

and still having high loading. I know its rtorrent that affecting it too.

---

