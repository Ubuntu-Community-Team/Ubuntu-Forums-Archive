---
title: "Recovering Corrupted JPEGs on SD Card"
date: 2010-10-12
forum: General Help
---

### Post by kiplingw on 2010-10-12
Hey forum,

I needed to use an SD card for something unusual today, but wanted to preserve all the photos on it. So I unmounted it and ran...

$ sudo dd if=/dev/mmcblk0 of=/home/kip/Desktop/Camera.bin bs=1MB

...to make a backup of the complete card, partitions included. I used the card for other purposes, umounted again, and then wrote back the image with...

$ sudo dd if=/home/kip/Desktop/Camera.bin of=/dev/mmcblk0 bs=1MB

I unmounted, removed the card, and then re-inserted to find most of the JPEGs corrupted. I can see some pixels, but they are all mangled.

I fear the blocksize (bs=1MB) may have been the culprit and should have been 512 (bytes) for a card containing a fat16 formatted partition.

Is there any way to recover the data?

---

### Post by renzokuken on 2010-10-13
could possibly try using Photorec. it was very successful when i managed to screw up a partition table once.

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

is a good start

---

### Post by kiplingw on 2010-10-13
I tried photorec and it was only able to recover the thumbnails. Of course, that's better than nothing. I think the problem was the read blocksize (bs=1MB) was the problem since the underlying filesystem of fat16 is in 512 byte blocks.

---

