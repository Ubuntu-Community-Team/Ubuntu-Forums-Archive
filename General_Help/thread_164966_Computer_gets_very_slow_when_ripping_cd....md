---
title: "Computer gets very slow when ripping cd..."
date: 2006-04-23
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-23
My computer gets very sluggish and laggy when ripping/reading cd's. How can I fix this ? Is there a way to check if I have DMA enabled on my cd drive ? I have it enabled on my HDD.

---

### Post by Computeruser on 2006-04-23
I had an issue with a CD/DVD player that came on some T30's. When recovering an image (multiple CD's), it would start reading slower and slower to the point of giving up. The remedy was to replace the CD player. A newer version of the CD/DVD player worked just fine. It was hard to tell initially if it was the computer or player.

---

### Post by JaiMeSX on 2006-04-23
:KS  By typing this you can activate DMA for your cdrom:
```
$ sudo hdparm -d1 /dev/cdrom
```

:KS  To keep settings:
   Edit /etc/hdparm.conf (as root of course) adding the following lines:
```
/dev/hdc {
    dma = on
}
```

good luck

---

