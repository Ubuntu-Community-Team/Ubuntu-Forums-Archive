---
title: "Resizing partition without formatting?"
date: 2010-01-14
forum: General Help
---

### Post by Cinemarxism on 2010-01-14
Hi,

This christmas I made a new partition on my hard drive, and installed Windows XP on it. However, because of space shortage on the disc (didn't bring my external HDD's with me) I could not "afford" to make the partition bigger than about 7GB. Turns out that's not quite enough.

So I thought I'd try to resize the partition. Booted from my Ubuntu LiveCD and entered the partition manager. I'm able to tell the program that I wan't to resize the Linux-partition (so it sets the now freed space as "unused", but when I chose to "resize/move" on the XP-partition I do not have any free space. Does this mean that I have to resize the Linux-partition (until now I didn't actually resize it, only set the job as "pending" hoping that I could select both to shrink the Linux-partition and extend the XP-partition in one session), or do I have to format the XP-partition and make a new one (larger this time), then reinstall XP?


[IMG]http://img695.imageshack.us/img695/6616/screenshot1rg.png[/IMG]

[IMG]http://img231.imageshack.us/img231/2503/screenshotzf.png[/IMG]

[IMG]http://img18.imageshack.us/img18/1629/screenshot2wx.png[/IMG]


/dev/sda1 is XP; /dev/sda2 is Linux Mint

Thanks

---

### Post by audiomick on 2010-01-14
you have to move the right then the left border of sda2 to the right into the free space (let gparted apply this) to that the free space is between sda1 and sda2, then you will be able to make sda1 bigger.

I hope you have backed up everything important before starting on this!

Edit: I think I have read that you should turn "round to cylinders" off for windows partitions.

---

### Post by Cinemarxism on 2010-01-14
Thank you! Almost embarrassing to miss something like that.

I have backed up everything of importance on external hard drives, so that should be covered. Will try this tonight.

---

### Post by audiomick on 2010-01-14
> **Cinemarxism said:**
> Thank you! Almost embarrassing to miss something like that.
Don't worry, took me a while to work it out the first time too.

> **Cinemarxism said:**
> I have backed up everything of importance on external hard drives, so that should be covered. Will try this tonight.
have fun, and good luck.

---

### Post by mister_playboy on 2010-01-14
Be aware that is operation can take several hours.

---

