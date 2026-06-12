---
title: "is there a program to free RAM?"
date: 2006-02-01
forum: General Help
---

### Post by closeyourwindows on 2006-02-01
I am looking for an application that monitors the RAM and that can free it when it is low.  I know there are win apps that will do it and was wondering if there was a gnome version?

---

### Post by kabus on 2006-02-01
Linux memory management does this automatically and very effectively.
If you really want to change the default behaviour you can do it by setting the swappiness.
Here's an explanation how it all works :

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by soulestream on 2006-02-01
kill 
killall 

Windows handles memory poorly and often holds on to RAM it shouldn't. Linux does a much better job of this. 

I have never seen any need for a "memory mananger" in windows, they always crash stuff and what is the point of installing an app that takes up memory, to free memory. They are kinda like registry cleaners, they usually do more harm than good.

soule

---

### Post by dcstar on 2006-02-01
[QUOTE=kabus]Linux memory management does this automatically and very effectively.
.....[/QUOTE]
Ain't it great when people realise they no longer need their "crutches" now that they are using a real OS...........               ;)

---

### Post by closeyourwindows on 2006-02-01
thanks for the info all, I was just curios becuase i did ```
Tasks:  87 total,   2 running,  85 sleeping,   0 stopped,   0 zombie
Cpu(s): 95.0% us,  5.0% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.0% siMem:    224476k total,   207200k used,    17276k free,     2960k buffers
Swap:   514040k total,    29088k used,   484952k free,    69272k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7033 root      16   0 34764  20m 7052 R 50.6  9.2  11:02.20 Xorg
13044 nate      15   0  104m  41m  17m S 16.9 18.8   1:33.58 firefox-bin
 7668 nate      15   0 15684 8468 6460 S 12.7  3.8   1:01.27 metacity
 7629 nate      15   0 19728 9028 6248 S  4.2  4.0   0:02.90 gnome-settings-13061 nate      15   0 31168  12m 8208 S  4.2  5.8   0:06.36 gnome-terminal
    1 root      16   0  1564  528  460 S  0.0  0.2   0:01.92 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.11 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.22 events/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 khelper
    5 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   86 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 kblockd/0
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.03 pdflush
  113 root      16   0     0    0    0 S  0.0  0.0   0:00.07 pdflush
  115 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  114 root      15   0     0    0    0 S  0.0  0.0   0:00.35 kswapd0
  700 root      15   0     0    0    0 S  0.0  0.0   0:00.01 kseriod

``` and then when I killed an application the memory was less. 
thanks for the reply and I will pass the dutchie on the left hand side.

---

### Post by soulestream on 2006-02-01
does X normally run at 50%?

looks like CPU is more of your problem than ram

soule

---

