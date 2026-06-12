---
title: "Mounting wrong partition"
date: 2006-03-17
forum: General Help
---

### Post by wbarnes on 2006-03-17
Hi,

When I mount /dev/hda5, ubuntu mounts what is actually /dev/hda6.  Not sure why but it seems to think the contents of my hda6 is hda5.  I have viewed the partition layout in qtparted and it shows hda5 as the correct partition except (I can tell via the size), but it is showing an incorrect number for "unused" space for this partition (ie. showing 1.8 gig available when really, I have 25 gig available on that partition).

Any ideas how I can fix this?

Thanks

Bill

---

### Post by taurus on 2006-03-17
What is the output of 
```

sudo fdisk -l /dev/hda

```

---

### Post by wbarnes on 2006-03-18
Here is the output from sudo fdisk -l /dev/hda:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1277    10257471    7  HPFS/NTFS
/dev/hda2            1278       11668    83465707+   f  W95 Ext'd (LBA)
/dev/hda3           11669       15315    29294527+  83  Linux
/dev/hda5            7654       11479    30732313+   7  HPFS/NTFS
/dev/hda6           11480       11668     1518111   82  Linux swap / Solaris
/dev/hda7            1278        7653    51215157    7  HPFS/NTFS
Partition table entries are not in disk order

hda5, hda6 and hda7 appear to be mixed up.   My large NTFS partition is supposed to be hda5 (but is showing up as hda7 above).  My smaller ntfs partition is supposed to be hda6 but is showing up as hda5.  The linux swap is supposed to be hda7 but is showing up as hda6.

The last line of the fdisk output indicates "Partition table entries are not in disk order" ..... is this an error message?

Any ideas?

---

### Post by wbarnes on 2006-03-18
Hi Folks,

After a bit of googling around the internet, I found the fix to my problem.  Had to fix the partition entries by running fdisk, selecting x for expert mode, selecting f for fix, selecting w for write changes, then reboot.  

Cheers

Bill

---

