---
title: "Sata HD performance"
date: 2006-06-09
forum: General Help
---

### Post by kverde on 2006-06-09
My twin Seagate sata drives seem slow.  The output from hdparm -tT for both is as follows:

/dev/sda:
 Timing cached reads:   1920 MB in  2.00 seconds = 959.67 MB/sec
 Timing buffered disk reads:  166 MB in  3.03 seconds =  54.78 MB/sec
kverde@black:/storage$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1932 MB in  2.00 seconds = 964.22 MB/sec
 Timing buffered disk reads:  166 MB in  3.01 seconds =  55.14 MB/sec

This is on a fresh Kubuntu 6.06 install. 

Any thoughts on the performance and how it could be improved?

---

### Post by briguy on 2006-06-09
This thread may help:

[http://www.ubuntuforums.org/showthread.php?t=157255&highlight=sata+dma](http://www.ubuntuforums.org/showthread.php?t=157255&highlight=sata+dma)

---

