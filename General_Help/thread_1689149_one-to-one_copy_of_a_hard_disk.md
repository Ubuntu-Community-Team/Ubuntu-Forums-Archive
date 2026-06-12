---
title: "one-to-one copy of a hard disk"
date: 2011-02-16
forum: General Help
---

### Post by HilliBilly on 2011-02-16
i have an old copy machine (canon gp225). the hard disk makes a whistling noise and i suppose it is just a question of time when it will bust.

i do have some stone-aged computers here and i think i could use one of this hard disks as a replacement.

but ... how do i get the operating system (probably unix/linux or similar) plus the content of the boot sector plus the software on this new hard disk? i think if i could do a one-to-one copy i might have a chance that i could replace the old hard disk and it will work.

any ideas are very much welcome :)

---

### Post by TeoBigusGeekus on 2011-02-16
Perhaps dd could do it:
```
dd if=/dev/sda1 of=/dev/sdb1
```
assuming that the old disk is sda1 and the new one is sdb1.

---

### Post by tredegar on 2011-02-16
A Canon canon gp225 is a photocopier, but that's OK.

**dd** will only work if the new disk is the same size, or larger than, the old disk.

As we do not know the partitioning or filesystem on the old disk, best to copy the **whole disk**, not just the first partition (ie **sda** not **sda1**).
 
dd does a bit-by-bit copy so if you copy the whole disk in this way, the boot sector, partition table etc. will all be copied as well as the data. Any extra spare space on your new disk will just be ignored (and become invisible until the day you repartition it).

If you only have cables for 2 disks (you say it is old, so I assume IDE), you'll need to plug in both your old and new disks, and boot to a live CD to make the copy.

Be _very_ careful when using **dd** that you are copying the right disk to the right disk. Or you'll have erased your original. This is not recoverable.

```
fdisk -l
``` will help you decide which disk is which, especially if you make sure the new disk is larger than the old one.

Assuming the old disk is /dev/sd[COLOR="Red"]a[/COLOR] (and, _please_ triple-check!)

```
dd [COLOR="Red"]if[/COLOR]=/dev/sd[COLOR="Red"]a[/COLOR] of=/dev/sdb
```

Wait for it to finish, plug the new disk into the photocopier, and see if it works.

Please let us know how you get on.

---

