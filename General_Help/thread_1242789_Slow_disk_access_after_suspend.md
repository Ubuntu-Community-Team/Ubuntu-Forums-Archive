---
title: "Slow disk access after suspend"
date: 2009-08-17
forum: General Help
---

### Post by mehturt on 2009-08-17
Sometimes my disk is too slow after laptop is resumed from suspend.
Right now, I'm getting:

$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1566 MB in  2.00 seconds = 783.13 MB/sec
 Timing buffered disk reads:   16 MB in  3.37 seconds =   4.74 MB/sec

I'm using Dell D630, Ubuntu 9.04.

---

