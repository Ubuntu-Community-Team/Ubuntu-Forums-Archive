---
title: "Used space on a fresh new ext4 partition"
date: 2010-09-09
forum: General Help
---

### Post by batsali on 2010-09-09
I used gparted to format a 360GB partition with ext4 and I expected it to have at most several hundred MB used for whatever reason by the file-system, but it said 18GB were used. How come? Are there any file-system settings I should have paid attention to?

---

### Post by Rubi1200 on 2010-09-09
Did you use GParted from the LiveCD?

Post the output of sudo fdisk -l (lowercase L not 1)

---

### Post by blur xc on 2010-09-09
I think that's normal.  It's there on ext3 partitions too, and I thinks it's space left for the file system journal.

I've seen that on every device I've formatted to ext3 & ext4.

BM

---

### Post by batsali on 2010-09-10
No, I didn't do it from the livecd

/dev/sda1   *          13        6528    52332544    7  HPFS/NTFS
/dev/sda3            6529       60802   435949345+   f  W95 Ext'd (LBA)
/dev/sda5           13043       60802   383625671   83  Linux
/dev/sda6            6529        6777     2000061   82  Linux swap / Solaris
/dev/sda7            6778       13042    50323581   83  Linux

---

### Post by nepenthe on 2010-10-31
> **batsali said:**
> I used gparted to format a 360GB partition with ext4 and I expected it to have at most several hundred MB used for whatever reason by the file-system, but it said 18GB were used. How come? Are there any file-system settings I should have paid attention to?
Yeah, I’m curious about this too. :)

---

### Post by mikewhatever on 2010-10-31
Ext3/4 reserve 5% of space for system processes, so that if the partition fills up, the system can still function. The setting was ok when partitions were 10-20GB, but reserving 18GB is way too much. Reserved space can be reclaimed as follows:

```
sudo tune2fs -m 0 /dev/sdXY
```

That will reset the percentage of reserved space to zero. If you want to keep some of the reserved space, use a number greater then zero (for example: 1, 0.1).

---

### Post by nepenthe on 2010-10-31
> **mikewhatever said:**
> Ext3/4 reserve 5% of space for system processes
Yeah, I already got that. Turns out, there are still about 15 gb used space on my freshly ext4-formatted 1-tb drive. Where does that come from?

---

