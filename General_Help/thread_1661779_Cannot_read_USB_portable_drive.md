---
title: "Cannot read USB portable drive"
date: 2011-01-07
forum: General Help
---

### Post by cedricf on 2011-01-07
Hello All

I removed my old 160Gb laptop drive to install a new 320Gb drive. The 160Gb drive is partitioned as follows: 20Gb unallocated partition, 115Gb ext3 partition (running ubuntu 10.04), and 5Gb swap.

I placed this drive in a portable enclosure so that I could retrieve data from it. The Disk Utility in Ubuntu recognizes the drive but the partitions are not recognized, shows unknown and the only option available is to format the volume. If I place the drive back into my laptop, the drive boots normally and data is accessible.

I have connected other portable USB drives and they work (NTFS formatted), so USB ports are not the problem.

Any ideas please?

Thanks

---

### Post by dino99 on 2011-01-07
so you need to watch logs about this "enclosure", seems that it use a chipset that have issue (not recognised)

---

