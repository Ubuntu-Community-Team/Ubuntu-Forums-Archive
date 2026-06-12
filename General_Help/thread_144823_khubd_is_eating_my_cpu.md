---
title: "khubd is eating my cpu"
date: 2006-03-15
forum: General Help
---

### Post by it.henrik on 2006-03-15
Hi fellow Ubuntu-lovers,

I have recently started to have some problems with khubd. It eats to much of my CPU for it to be healthy, and it does that constantly. I cant get any usb-devices to work either when khubd is freaking out. 

I cant 
sudo kill $khubd-pid
or
sudo kill -9 $khubd-pid

it never dies :)

Whats wrong, and what can I do to make it stop? The only thing that I figured out my self is rebooting.. but then I start to feel like im running windows again.

any help would be MUCH appreciated (non-native english speaker here :) )

this is how my top looks like

henrik@ubuntu-Latten:~$ top

top - 10:49:40 up 18:20,  4 users,  load average: 1.55, 1.44, 1.47
Tasks: 108 total,   2 running, 106 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.5% us, 54.3% sy,  0.0% ni, 29.4% id,  1.1% wa,  1.6% hi,  2.1% si
Mem:    516260k total,   507740k used,     8520k free,    29244k buffers
Swap:   530104k total,   367504k used,   162600k free,   165644k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1913 root      25   0     0    0    0 R 98.6  0.0 594:01.53 khubd
    1 root      16   0  1564  444  420 S  0.0  0.1   0:02.39 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.72 events/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.11 kacpid
  113 root      10  -5     0    0    0 S  0.0  0.0   0:00.49 kblockd/0
  140 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  139 root      15   0     0    0    0 S  0.0  0.0   0:03.06 kswapd0
  725 root      15   0     0    0    0 S  0.0  0.0   0:00.02 kseriod
 3055 root      10  -5     0    0    0 S  0.0  0.0   0:00.27 reiserfs/0
 3189 root      11  -4  1664  400  400 S  0.0  0.1   0:00.17 udevd
 4380 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 5782 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 5792 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 5802 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 5889 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0

---

### Post by PawnerGaSp on 2008-03-17
Yes I have been having this issue too, and after a while, all my USB devices die.  Any ideas people?  Because, well, I kinda need my keyboard.

---

### Post by rbertran on 2008-03-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/79539](https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/79539) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same error. 

Can you check if your problems are related with these ones:
[https://lists.ubuntu.com/archives/desktop-bugs/2007-January/070720.html](https://lists.ubuntu.com/archives/desktop-bugs/2007-January/070720.html)
[https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/79539](https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/79539)

I guess that my problem is the webcam and ekiga too...

Related background about khubd:
[http://www.linuxjournal.com/node/8093/print](http://www.linuxjournal.com/node/8093/print)

I will keep looking about a solution to this problem...

---

