---
title: "hard disk working at half speed during boot?"
date: 2010-10-22
forum: General Help
---

### Post by criball on 2010-10-22
Hello everybody,

I've recently updated my ubuntu lucid to maverick (32bit). However I noticed a strange issue at boot. My boot time is increased more than three times (tried to reprofile, but with no improvement) from 24s to 1.23min.
After some bootcharting, I noticed that the disk utilization during maverick boot seems to be at 50% for most of the time and also the cpu seems to work at half speed for most of the time...
My laptop is an asus m51sn, intel t8300, nvidia geforce 9500m gs, 3gb ram, 500Gb WD scorpio blue hdd.

bootchart for maverick:
[[img]http://t1.pixhost.org/thumbs/1490/4300663_thilkhelex-maverick-20101021-6.png[/img]](http://www.pixhost.org/show/1490/4300663_thilkhelex-maverick-20101021-6.png)

bootchart for lucid:
[[img]http://t1.pixhost.org/thumbs/1490/4300674_thilkhelex-lucid-20100705-3.png[/img]](http://www.pixhost.org/show/1490/4300674_thilkhelex-lucid-20100705-3.png)

Thanks in advance for any help...

P.S. Funny note, my atom270 netbook with maverick and pretty much the same software installed boots in 17s ](*,)

---

### Post by P4man on 2010-10-22
You are comparing apples to oranges.
The maverick bootchart includes loading Xorg and all your gnome apps, your lucid bootchart stops before Xorg. Maverick seems to take about the same time as lucid to reach Xorg, both about 27s.

---

### Post by criball on 2010-10-22
Ok, maybe it's not three times, still if you look at when gconf and metacity are loaded its around 35s in maverick and ~23s in lucid...
Beside, the time to get to an usable gdm is noticable more than it used to be under maverick.
However, as the post subject says, what worries me is the hdd utilization graph, why is always at one half?

---

