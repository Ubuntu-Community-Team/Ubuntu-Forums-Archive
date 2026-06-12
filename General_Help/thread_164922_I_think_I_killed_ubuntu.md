---
title: "I think I killed ubuntu"
date: 2006-04-23
forum: General Help
---

### Post by Zyphrexi on 2006-04-23
for whatever reason, /dev/hdb1 (my dapper partition) was listed as /dev/hdb3 under breezy, using System>Admin>Disks I formatted /dev/hdb3 as a vfat. /dev/hdb1 was formatted and everything was lost, but some wierdness occurred that makes me think it's possible that I might be able to recover it.

/dev/hdb3 (which is in actuality /dev/hdb1) was listed as having 6.7 gb in the partition. (but it actually has well over 100gigs)

secondly the actual formatting process took only a few seconds.

What happened and how can I recover it, can I even recover it? I had everything on that partition.

Secondly I'd like to know why breezy looked at /dev/hdb1 and called it /dev/hdb3 and claimed it had only 6.7gigs?

---

### Post by aysiu on 2006-04-23
I'm not sure I can really solve your problem, but someone else may be able to if you go to Applications > Accessories > Terminal and post here the output of this command: ```
sudo fdisk -l
```

---

### Post by Zyphrexi on 2006-04-23
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       13729   110278161   83  Linux
/dev/hdb2           13730       23455    78124095   83  Linux
/dev/hdb3           23456       24281     6634845   83  Linux
/dev/hdb4           24282       24321      321300    5  Extended
/dev/hdb5           24282       24321      321268+  82  Linux swap / Solaris

---

