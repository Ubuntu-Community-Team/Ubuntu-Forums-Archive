---
title: "dmraid - 4disk raid0 = slow?"
date: 2010-03-15
forum: General Help
---

### Post by SlugSlug on 2010-03-15
Hi 

I have 4 x 160GB sata drives on a PCI raid controller setup as raid0.

I installed dmraid and the four drives show as one which is now mounted, ext4

I ran 

sudo hdparm -t /dev/mapper/sil_bgadcabgffcg

which shows
/dev/mapper/sil_bgadcabgffcg
 Timing buffered disk reads:  292 MB in  3.01 seconds =  96.88 MB/sec
------------------------------------------------------------------------------------
which is **slower **than one of my single sata drives

which shows
/dev/sdb:
 Timing buffered disk reads:  324 MB in  3.01 seconds = 107.62 MB/sec
------------------------------------------------------------------------------------


whys that?

---

### Post by SlugSlug on 2010-03-21
sorry to bump

---

### Post by sandyd on 2010-03-21
what RAID controler are you using?

if its jmicron, get another controler, since I see a lot of people with jmicron RAID performance Issues

---

### Post by SlugSlug on 2010-03-21
05:02.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)

---

