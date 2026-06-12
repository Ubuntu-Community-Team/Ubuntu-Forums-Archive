---
title: "Something is using way too much memory"
date: 2009-11-02
forum: General Help
---

### Post by ravynchylde1960 on 2009-11-02
From the top command:
leslie@leslie-desktop:~$ top                                                                         
top - 18:43:21 up 1 day, 21:42,  2 users,  load average: 0.05, 0.07, 0.02
Tasks: 190 total,   3 running, 187 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.3%us,  1.1%sy,  0.0%ni, 95.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3539476k total,  2735452k used,   804024k free,   163260k buffers
Swap: 10369916k total,    13980k used, 10355936k free,  1552900k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1564 root      20   0  393m 186m  33m S    5  5.4 166:17.14 Xorg
 8582 leslie    20   0  218m  25m  15m R    3  0.7   0:09.39 npviewer.bin
 2080 leslie    20   0  650m  86m  31m S    2  2.5  11:21.66 plasma-desktop
 2164 leslie    20   0  342m 6164 4104 S    2  0.2  23:38.89 pulseaudio
 8542 leslie    20   0  970m 116m  36m R    2  3.4   0:14.87 firefox
 2032 leslie    20   0  442m  32m  22m S    1  0.9  47:50.06 kwin
 8156 leslie    20   0  343m  23m  14m S    1  0.7   0:02.23 konsole
 8698 leslie    20   0 1231m 128m  13m S    1  3.7   0:13.18 java
 8765 leslie    20   0 19132 1384  980 R    0  0.0   0:00.09 top
    1 root      20   0 19440 1620 1148 S    0  0.0   0:00.95 init

What is adding up to 2.8 GIGS of memory?...

When I did not have Firefox or the Java applet running:

top - 18:38:54 up 1 day, 21:38,  2 users,  load average: 0.18, 0.06, 0.02
Tasks: 187 total,   1 running, 186 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.1%us,  1.0%sy,  0.0%ni, 96.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3539476k total,  2515328k used,  1024148k free,   162800k buffers
Swap: 10369916k total,    13980k used, 10355936k free,  1544120k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                 
 2032 leslie    20   0  442m  32m  22m S   10  0.9  47:40.14 kwin                                    
 1564 root      20   0  390m 184m  31m S    1  5.3 165:59.04 Xorg                                    
 2080 leslie    20   0  650m  86m  31m S    1  2.5  11:17.65 plasma-desktop                          
 8521 leslie    20   0 19132 1384  980 R    1  0.0   0:00.41 top                                     
 8156 leslie    20   0  343m  23m  14m S    0  0.7   0:02.02 konsole                                 
    1 root      20   0 19440 1620 1148 S    0  0.0   0:00.95 init

---

### Post by pastalavista on 2009-11-02
It looks like Xorg is working way too hard. Try this command in terminal ```
sudo dpkg-reconfigure xserver-xorg
``` then log off and back on and run top again.

---

### Post by unamanic on 2009-11-02
File Caching/buffers;
Linux reads files into memory so that if they are accessed again, they can be ready quickly.  If an application needs the space to run then the files are taken out of memory and must be read from the disk the next time it is read.

Next time you want to check memory utilisation I reccomend using "free -m" (the "m" is for megs)
[unamanic@gimli] ~ $ free -m
```

             total       used       free     shared    buffers     cached
Mem:          3924       2983        941          0         65       2237
-/+ buffers/cache:        679       3244
Swap:        19999         45      19954

```This shows that 2983mb of RAM is "used" but only 679mb of RAM is used for applications, the rest is for caching.

---

### Post by ravynchylde1960 on 2009-11-02
Okay, so using that command

             total       used       free     shared    buffers     cached
Mem:          3456       2780        676          0        164       1477
-/+ buffers/cache:       1138       2317
Swap:        10126         13      10113

How do I drop the cache down, or can I? I have 4G of memory on this machine and ALL my programs are running slow.

---

### Post by ravynchylde1960 on 2009-11-02
As for the xorg command, it did the same thing every other time I've tried it.

Absolutely nothing.

---

### Post by unamanic on 2009-11-02
> **ravynchylde1960 said:**
> Okay, so using that command

             total       used       free     shared    buffers     cached
Mem:          3456       2780        676          0        164       1477
-/+ buffers/cache:       1138       2317
Swap:        10126         13      10113

How do I drop the cache down, or can I? I have 4G of memory on this machine and ALL my programs are running slow.

You don't need to, disk caching is used transparently.  Your CPU utilisation looks good, so I'd suspect a disk i/o bottleneck.  If you are running with desktop effects turned on, you may try turning them off to see if that helps.  But to find out about a disk i/o problem:

```

sudo aptitude install atop
sudo atop

```

give atop a little bit of time and then see if any of teh resources in the top secion are ove utilized.

---

### Post by ravynchylde1960 on 2009-11-02
Well, the atop gave me this:

ATOP - leslie-desktop     2009/11/02  20:49:24               10 seconds elapsed
PRC | sys   0.47s | user   1.51s | #proc    191 | #zombie    0 | #exit      0 |
CPU | sys      5% | user     15% | irq       0% | idle    381% | wait      0% |
cpu | sys      3% | user      7% | irq       0% | idle     89% | cpu002 w  0% |
cpu | sys      1% | user      6% | irq       0% | idle     93% | cpu003 w  0% |
cpu | sys      0% | user      0% | irq       0% | idle    100% | cpu001 w  0% |
cpu | sys      1% | user      1% | irq       0% | idle     99% | cpu000 w  0% |
CPL | avg1   0.05 | avg5    0.06 | avg15   0.00 | csw    14300 | intr    5068 |
MEM | tot    3.4G | free  717.5M | cache   1.5G | buff  168.5M | slab  166.1M |
SWP | tot    9.9G | free    9.9G |              | vmcom   1.5G | vmlim  11.6G |
DSK |         sda | busy      0% | read       0 | write     22 | avio    0 ms |
NET | transport   | tcpi       5 | tcpo       5 | udpi       0 | udpo       0 |
NET | network     | ipi        5 | ipo        5 | ipfrw      0 | deliv      5 |
NET | eth0     0% | pcki       5 | pcko       5 | si    0 Kbps | so    0 Kbps |

  PID  SYSCPU  USRCPU  VGROW  RGROW  RDDSK  WRDSK  ST EXC S  CPU CMD     1/1
10879   0.02s   0.59s     0K -1568K     0K     0K  --   - S   6% java
 1564   0.14s   0.41s     0K     0K     0K     0K  --   - S   5% Xorg

And just before I copied it, the java was at 12% cpu. Maybe it's a java chat applet problem with FF?

---

### Post by unamanic on 2009-11-02
It could be java, are you using the sun JRE or the open one?  I've had better luck with the sun JRE for speed in general.  

You may want to look into whether or not kopete will support the chat protocol that your java applet is using.  

You may also want to ensure smooth scrolling is turned off in firefox, it can cause firefox to respond slowly.

---

