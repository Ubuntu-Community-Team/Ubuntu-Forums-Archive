---
title: "Formatting 2nd NTFS hard drive"
date: 2009-12-17
forum: General Help
---

### Post by klnyc on 2009-12-17
Hi guy,

   Okay, here I am trying to reformat my 2nd HD. This drive is still NTFS format.  I follow the steps How To Format new HD, but still no luck. I keep getting an error after I selected "W".  This what the error says.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe( 8 ) or kpartx( 8 )
Syncing disks.

/dev/sbd1 is my 2nd hd btw.  Any help greatly appreciated!!!!

---

### Post by lidex on 2009-12-17
> The new table will be used at
the next reboot or after you run partprobe( 8 ) or kpartx( 8 )

Have you tried running those commands?

---

### Post by klnyc on 2009-12-17
> **lidex said:**
> Have you tried running those commands?

Yup, I used it and still no help.

---

### Post by lidex on 2009-12-18
Try this in a terminal and post the results:
```
sudo fdisk -l
```

---

### Post by klnyc on 2009-12-18
> **lidex said:**
> Try this in a terminal and post the results:
```
sudo fdisk -l
```


I got it...
I was doing "fdisk /dev/sdb1" . Instead of "fdisk /dev/sdb"

---

