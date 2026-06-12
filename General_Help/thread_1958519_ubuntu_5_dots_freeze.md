---
title: "ubuntu 5 dots freeze"
date: 2012-04-14
forum: General Help
---

### Post by 700 on 2012-04-14
System: Ubuntu 11.10
Graphics: ASUS Radeon HD6970
Driver: ARI/AMD proprietary FGLRX graphics driver [activated]

Problem: 
'Ubuntu 5 dots' running for 5 minuts every start of the system.
[http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu10artwork-large_003.jpg](http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu10artwork-large_003.jpg)

Googled solutions didn't help. Everything else working very well (so far), except CPU sensor showing 19*C instead of 37*C on 'hardinfo'.

---

### Post by dino99 on 2012-04-14
edit the boot grub menu line to remove "quiet splash" before booting; that way you will see all the boot comments and let you know what is the problem

---

### Post by QIII on 2012-04-14
... and post back the last few lines.

By the way, if your CPU is one from AMD, they are infamous for returning low temp results.

Generally not 20C.  lm-sensors querying K10temp usually returns about 10C low.

---

### Post by 700 on 2012-04-14
Unfortunately I've never had to use grub, so I'll need to reed a manual about that, till I give any decent answer. 
My grub messages disappeared after 5 seconds and I don't know how to get them back (Page Up doesn't help).

After about 200 seconds and later something like that appear:
> task swapon:431 blocked for more than 120 seconds
"echo 0 > /proc/sys/kernel...
...
SP5100 TCO timer: mmio address 0xbafe00 already in use


---

