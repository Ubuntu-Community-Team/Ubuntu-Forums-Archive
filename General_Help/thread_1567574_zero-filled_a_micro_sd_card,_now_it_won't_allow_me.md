---
title: "zero-filled a micro sd card, now it won't allow me to repartition?"
date: 2010-09-04
forum: General Help
---

### Post by Brinstar on 2010-09-04
i have an 8gb sandisk micro sd card that i was having problems with, so i decided to zero it out, problem is now i can't repartition it.

i have tried gparted, the disk won't appear, but when it is attached, i can see a /dev/sdb in devices that isn't there otherwise.

is it possible to create a new partition table on this, and how?

also i am trying to 'sudo mkfs.vfat /dev/sdb' but it is saying 

'/dev/sdb: No medium found'

---

### Post by bodhi.zazen on 2010-09-04
Depends on what is wrong with it. If the drive failed, no.

Try fdisk

```
fdisk /dev/sdxy
```

Type m for help

Try the o option or create a new partition with n

---

### Post by harrismh777 on 2010-09-04
> **Brinstar said:**
> i have an 8gb sandisk micro sd card that i was having problems with,

You gave yourself the answer.

If fdisk will not partition the drive ( or worse, maybe the device cannot be seen ) there is probably a serious hardware difficulty with the device... not fun, but happens.

---

### Post by Brinstar on 2010-09-04
> **harrismh777 said:**
> You gave yourself the answer.

If fdisk will not partition the drive ( or worse, maybe the device cannot be seen ) there is probably a serious hardware difficulty with the device... not fun, but happens.

yeah i am starting to think that is the case, it could at least be seen before, now running even dd i get

```
dd: opening `/dev/sdb': No medium found
```

still i want to be sure it is the card and not something else, so will probably try this procedure on another micro sd card i have lying about. possibly unwise, but i feel like i am learning something at least! ;)

---

### Post by efflandt on 2010-09-04
If you zeroed the microSD, it now has no partition table or info at all.  Use gparted to create an **msdos partition table**.  Then you should be able to partition it.  I often had that problem when some version of USB Startup Disk Creator defaulted to formatting the drive instead of the partition.

---

### Post by Brinstar on 2010-09-04
> **efflandt said:**
> If you zeroed the microSD, it now has no partition table or info at all.  Use gparted to create an **msdos partition table**.  Then you should be able to partition it.  I often had that problem when some version of USB Startup Disk Creator defaulted to formatting the drive instead of the partition.

i tried that, even gparted couldn't see the drive

it is now in the bin and i am using a different micro sd, end of story :)

this is the 2nd 8gb microsd that has failed on me, must stay away from these in future. i always wondered how they manage to store so much data on 1/4 the size of a postage stamp.

---

