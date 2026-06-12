---
title: "Fix bad sectors on hard disk."
date: 2009-09-08
forum: General Help
---

### Post by Woody1987 on 2009-09-08
I have a 1TB disk with 3 partitions.

> Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b5d61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      106214   853163923+  83  Linux
/dev/sdc2          106215      118962   102398310   83  Linux
/dev/sdc4          118963      121601    21197767+   7  HPFS/NTFS

The two linux partitions are formatted to ext4. I have found out that this disk has bad sectors. How do i go about trying to fix this? Is it possible?

---

### Post by bodhi.zazen on 2009-09-08
> **Woody1987 said:**
> I have a 1TB disk with 3 partitions.

The two linux partitions are formatted to ext4. I have found out that this disk has bad sectors. How do i go about trying to fix this? Is it possible?

That output did not show bad sectors.

Generally bad sectors are handled at a low level, by the disk controller, and can not be fixed.

---

### Post by Woody1987 on 2009-09-09
The output was to simply show the partitions. I am 100% certain that it has bad sectors. Can anything be done?

---

### Post by QIII on 2009-09-09
You might start here...

[https://answers.launchpad.net/ubuntu/+question/10851](https://answers.launchpad.net/ubuntu/+question/10851)

but they can't be "fixed".

---

### Post by BslBryan on 2009-09-09
You have a couple of options. :-)

1. You can download the HD diagnostic utility from your manufacturer's website.  Most of the main HDD manufacturers make them freely available. 

2. You can run [badblocks](http://www.die.net/doc/linux/man/man8/badblocks.8.html) and save the bad sectors to a file, then use [mkfs](http://www.die.net/doc/linux/man/man8/mkfs.8.html) to make sure the filesystem won't use those sectors.

```
# mkfs -ct <filesystem> <partition device file>
```

But that's all I've been able to find.

---

### Post by QIII on 2009-09-09
If the disk got jangled and a head hit a platter, you may be lucky and have an isolated problem.

If one of your heads is borked, you're going to continue to drag it on a platter and ruin at least that platter, if not the whole drive.

If you find that you get more and more sector damage, it may be time to recover what you can and head down to BestBuy.

---

### Post by BslBryan on 2009-09-09
> **QIII said:**
> If the disk got jangled and a head hit a platter, you may be lucky and have an isolated problem.

If one of your heads is borked, you're going to continue to drag it on a platter and ruin at least that platter, if not the whole drive.

If you find that you get more and more sector damage, it may be time to recover what you can and head down to BestBuy.

+1. 

Even though badblocks is a temporary way to get around using the bad sectors, there is a reason why the computer warns you against them.  In the end, your HD is failing, and simply purchasing a new one is the best choice all around.

---

### Post by oboedad55 on 2009-09-09
Are you by any chance running Karmic Koala? If so, the hard disk test gizmo is borked. Don't trust it. You can do a search, there is lots of anecdotal evidence.

---

