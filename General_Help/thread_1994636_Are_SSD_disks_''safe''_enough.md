---
title: "Are SSD disks ''safe'' enough?"
date: 2012-06-03
forum: General Help
---

### Post by GreatDanton on 2012-06-03
My question is: Are SSD disks 'safe' enough or not. With safe I mean, that it will not delete your data itself. I heard some rumors, that SSD disks are very good, but one day you can lost all your data. Is that true or not?

Thanks in advance.

---

### Post by HermanAB on 2012-06-03
All disks are like you described.

SSDs are commonly used in high stress, high vibration environments where mechanicall disks cannot work at all.  For example ships and helicopters.  Think about that a moment.

---

### Post by 3rdalbum on 2012-06-03
> **GreatDanton said:**
> My question is: Are SSD disks 'safe' enough or not. With safe I mean, that it will not delete your data itself. I heard some rumors, that SSD disks are very good, but one day you can lost all your data. Is that true or not?

Thanks in advance.

Not true.

Early SSDs had a low mean-time-before-failure (MTBF), so if you wrote and rewrote data to the SSD too much it would start becoming unable to write to certain cells of memory.

Today's SSDs have a high MTBF, so it takes a very long time to get the SSD to that state of being unwritable. Also, SSDs do wear-levelling to increase the life of the drive too. There are other clever things that operating systems and drive controllers do too, like delaying writes to prevent data being quickly written and overwritten to the SSD.

I think these days a good SSD will be rated at something like ten years of normal use before cell failure. You're actually more likely to get normal filesystem corruption than you are to have the SSD fail, and filesystem corruption happens just as often (or as rarely) on hard disks.

In short, SSDs are safe for years and years.

---

### Post by GreatDanton on 2012-06-03
Thanks for replies. I think this thread could be marked as solved :)

---

