---
title: "memory usage"
date: 2010-12-22
forum: General Help
---

### Post by mattman85 on 2010-12-22
I was poking around in my ubuntu box using SSH at work (need something to do while on break), and I wanted to see what processes were running. I ran 'top' and noticed that Ubuntu's using almost 75% of my total RAM. Here is what top is reporting:

```
top - 11:29:47 up 1 day, 18:53,  2 users,  load average: 0.10, 0.14, 0.15
Tasks: 165 total,   1 running, 164 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.7%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   1929992k total,  1288444k used,   641548k free,    98432k buffers
Swap:  3646460k total,    22804k used,  3623656k free,   824304k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  591 matt      20   0  2620 1124  832 R    1  0.1   0:01.80 top
    7 root      20   0     0    0    0 S    0  0.0   4:16.00 ksoftirqd/1
   10 root      20   0     0    0    0 S    0  0.0   0:02.96 events/1
 1193 root      15  -5     0    0    0 S    0  0.0   1:31.30 kslowd001
 1517 matt      20   0  3908  312  288 S    0  0.0   1:08.45 syndaemon
 1955 matt      20   0 33932  16m 1596 S    0  0.9   4:38.91 ubuntuone-syncd
 8580 root      20   0  130m  10m 4608 S    0  0.5   3:07.38 firestarter
    1 root      20   0  2864 1212  828 S    0  0.1   0:00.87 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:05.30 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.03 migration/1
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      20   0     0    0    0 S    0  0.0   0:01.94 events/0
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper

```I'm not really sure how to read this, in regards to what amount of mem a certain process is using. I just know that after I saw this, I SSH-VNCed into the box, and no programs are open. I have Firestarter loaded in the tray, so that my firewall is on, and I'm on wifi at home. Those are the only things that would be running at the moment.

Is ubuntu really that much of a mem hog, or could it be something running?

---

### Post by uRock on 2010-12-22
Most of the RAM being used is for cache and buffers that will be dumped when another program needs the RAM.

---

### Post by oldos2er on 2010-12-22
[http://www.linuxatemyram.com/index.html](http://www.linuxatemyram.com/index.html)

---

### Post by mattman85 on 2010-12-22
@uRock: Thanks for the fast and simple,understandable response!

@oldos2er: thanks for the informative website!

that site makes me think I'm more of a newbie than I thought I was :sad: Oh well, I guess the only way you learn is by asking questions!

---

