---
title: "Ubuntu keeps freezing"
date: 2011-09-04
forum: General Help
---

### Post by chris153 on 2011-09-04
I have a freshly installed ubuntu 11.04 that im trying to use, but every so often (every couple of hours) when I am just surfing the web, ubuntu will freeze. I can move the mouse around, but cannot click on anything, nothing is responsive. Im new to linux, so im not even sure if there is some kind of ctrl+alt+delete equivalent that i should be hitting when this happens, or anything else. any ideas are appreciated. thanks!

---

### Post by Mark Phelps on 2011-09-05
If it takes a couple of hours to happen, and it always happens around the same timeframe since you first booted your PC, then it's likely to be a heat issue -- especially if you're running a laptop that came with Windows on it and you replaced that with Ubuntu.

---

### Post by DataSpy on 2011-09-05
[laptop cooler]("http://www.amazon.com/Cooler-Master-NotePal-Notebook-R9-NBC-8PCK-G/dp/B003ZMF27G/ref=sr_1_4?ie=UTF8&qid=1315264328&sr=8-4")

:)

---

### Post by paintthemonkey on 2011-09-16
I have the same issue and do not believe it's a heat problem . 

I am running unbuntu 11.4 
on a HP Z400 workstation 

at first i thought it was an issue with our LTO4 tape drive crashing but it has been doing the same to me now when the drive is off and i'm just mucking about .


screen will freeze  nothing is click-able but the mouse will move.
 in more severe crashes even the mouse is frozen and a hard boot is required . 

-HP-Z400-Workstation:~$ top

top - 10:51:33 up 13 min,  2 users,  load average: 0.04, 0.09, 0.08
Tasks: 172 total,   1 running, 170 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.5%us,  0.4%sy,  0.0%ni, 98.9%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   6107356k total,  1008652k used,  5098704k free,    70324k buffers
Swap: 17890300k total,        0k used, 17890300k free,   299904k cached

---

### Post by luckyu on 2011-09-16
Did you install that latest updates after you fresh install?

Also when it crashes again pres Crt-Alt-f4 and login and see if you have terminal access. If you can do that I could such simply be that a program on Ubuntu is crashing and not Ubuntu itself and to fix that program is don't use that program or update it so it doesn't.

---

### Post by paintthemonkey on 2011-09-16
> **luckyu said:**
> Did you install that latest updates after you fresh install?

Also when it crashes again pres Crt-Alt-f4 and login and see if you have terminal access. If you can do that I could such simply be that a program on Ubuntu is crashing and not Ubuntu itself and to fix that program is don't use that program or update it so it doesn't.

I've done a clean  install and I  keep this box updated. 
LTO4 drive is run via command line , freeze around 4 hours . , 
chrom(ium) and firefox freeze after about 30 min  - 2 hours 

Actually i've been goggling  it appears to be a issue with the 2.6.38-10 generic kernel.
lots of people are having a similar freezing issue with Natty running this kernel.

.39 is out ,but i'm not sure if i want to go to that or do a full 3.0 update reading on 3.0 now...

---

