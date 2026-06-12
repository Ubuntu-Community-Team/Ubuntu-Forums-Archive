---
title: "Upgrading directly from 8.04 to 9.10"
date: 2009-11-05
forum: General Help
---

### Post by OldGrantonian on 2009-11-05
I created a dual-boot Ubuntu partition on my Vista laptop. I tried Ubuntu 8.04.2 LTS Hardy for a few days, then upgraded to 9.10 Karmic.

Because I had hardly any files to save, I simply deleted the Ubuntu partition and started again. This was to allow Ubuntu to do everything automatically, rather than me having to make decisions about which disk format to use, swap space, etc, etc.

The reason that I deleted the partition, rather than simply overwrite the Ubuntu, is that the following link shows that I can only upgrade 8.04 > 8.10 > 9.04 > 9.10:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

I assume that for future updates, I will simply update incrementally. But I would be grateful to know how the experts would have upgraded directly from 8.04 to 9.10.

BTW:  I have a massive external drive with plenty of free space :)

---

### Post by zvacet on 2009-11-05
> But I would be grateful to know how the experts would have upgraded directly from 8.04 to 9.10.

It is not possible to do direct upgrade from Hardy to Karmic.it will be possible with Lucid because that version will be LTS too.In your case you can install Karmic on top of existing Ubuntu partition.It will be good to have separate home patition if you have enough free space.In that case root should be max 10GB and you can give rest of free space for home partition(except for few GB for swap).With home partition your data/files and settings will be safe if you chosse to do fresh install in future.

---

### Post by OldGrantonian on 2009-11-08
> **zvacet said:**
> It will be good to have separate home patition if you have enough free space.In that case root should be max 10GB and you can give rest of free space for home partition(except for few GB for swap).With home partition your data/files and settings will be safe if you chosse to do fresh install in future.

I'm no expert, but that sounds like excellent advice :)
.

---

