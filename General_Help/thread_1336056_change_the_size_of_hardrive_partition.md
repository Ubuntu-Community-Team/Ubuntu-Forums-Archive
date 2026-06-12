---
title: "change the size of hardrive partition?"
date: 2009-11-24
forum: General Help
---

### Post by jaywilsonbmx on 2009-11-24
im running ubuntu9.10 karmic dual boot with win7 32bit
i have a 80gb hardrive partitioned half for windows half for Linux
i wanted to change it so i had more space for windows and less for linux
how do i go about doing that?

---

### Post by hal10000 on 2009-11-24
use gparted

---

### Post by konradpiskorz on 2009-11-24
First you're going to have to boot into a live CD and make sure that your partitions remain unmounted, otherwise unmount it yourself.

At this point qtparted or gparted are the easiest and probably safest way to go about resizing, you can right click on a partition in the program and choose to resize it.

If the live CD doesn't come with either of these programs go into the terminal and install them with

sudo apt-get install gparted


I can also suggest the Gparted livecd which is always handy to have around.

[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)

---

### Post by audiomick on 2009-11-24
Gparted is on the live CD. You can also make yourself a Gparted live CD
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
which some people seem to think is better, and should stop things being mounted when you boot from the CD, if that turns out to be a problem. You can't alter a partition that is mounted.

Most important:

[SIZE="5"][COLOR="Red"]**BACKUP EVERYTHING IMPORTANT FIRST!!!**[/COLOR][/SIZE]

Gparted works well, but things can always go wrong...

---

