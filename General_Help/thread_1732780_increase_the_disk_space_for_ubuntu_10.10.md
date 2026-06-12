---
title: "increase the disk space for ubuntu 10.10"
date: 2011-04-18
forum: General Help
---

### Post by rekharajct on 2011-04-18
I have installed ubuntu 10.10 inside windows(windows 7)  from the ubuntu  home edition CD.I have allocated a disk space of 12GB.How could I  increase the disk space to 20 GB with out reinstalling ubuntu ?

---

### Post by drs305 on 2011-04-18
One way would be to move /home to it's own dedicated (virtual) partition. It's described in the Wubi Wiki. You can also use another procedure, LVPM, which has a link in the same section.
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")

If you scroll up one topic in the link, it describes how to migrate Wubi to its own real partition.

---

### Post by Rubi1200 on 2011-04-18
As well as the method suggested by drs305, you can also take a look here for tips on how to resize the root.disk:
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by drs305 on 2011-04-18
Rubi1200,

You or *bcbc* should get that put into the wiki. :-)

---

