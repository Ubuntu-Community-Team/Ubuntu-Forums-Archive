---
title: "Please help me regarding deletion of all partition in harddisk."
date: 2010-09-17
forum: General Help
---

### Post by justpratik on 2010-09-17
Hello, 

    Thank you for reading this post.
    

  " yesterday i had decided to format one partition. so on i have choose the partition in disk utility and the hit the format button. then ubuntu has asked me to select mbr method. once i have entered the method my all partition were vanished rather then one. including the recovery partition"
   my machine is samsung n140 ATOM. i was using windows xp/7/ubuntu at same time . please help me.

---

### Post by srs5694 on 2010-09-17
It sounds like you selected the option to create a partition table, not to "format" a partition.

AFAIK, the simplest solution is to run [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) from an emergency boot disk, like [PartedMagic](http://partedmagic.com) or [System Rescue CD.](http://www.sysresccd.org) This tool scans a disk for filesystem markers, and can build a new partition table around them.

Good luck.

---

