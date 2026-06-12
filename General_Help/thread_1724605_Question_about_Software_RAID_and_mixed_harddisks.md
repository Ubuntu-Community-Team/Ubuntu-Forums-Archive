---
title: "Question about Software RAID and mixed harddisks"
date: 2011-04-08
forum: General Help
---

### Post by apollyon_haj on 2011-04-08
Hi,
I would like to mirror some of my partitions (i.e. /home) with a software RAID. My primary harddisk is a Western Digital WD20EARS with Advanced Factor (4kB Sectors). The secondary disk is a Samsung HD103UJ with old sector-style (512B). Is it possible to set up a RAID 1 containing a partition with advanced factor an a partition with old sector-style or do both partitions have do be in the same sctor-style?
Thanks in advance,
Jo.

---

### Post by seawolf167 on 2011-04-08
I think you should be ok provided you setup the raid and initialize with your smaller disk. Here is the official Ubuntu [how-to]("https://help.ubuntu.com/community/Installation/SoftwareRAID") for setting up RAID.

Unless you are really dead set on making a RAID system, you could just as easily mirror your system automatically with a crontab entry that copies/mirrors with something like *dd *or *rsync*

---

