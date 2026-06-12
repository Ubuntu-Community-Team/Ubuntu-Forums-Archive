---
title: "Deleting Partition Table"
date: 2011-08-07
forum: General Help
---

### Post by Tarvok on 2011-08-07
I recently received a shiny new Commodore 64 throwback machine, and had a few problems I believe may have been hard drive problems when I attempted to install Ubuntu on it. There is nothing on it yet other than an earlier version of Ubuntu I'd like to replace with the current version. But before I do that, I'd like to do a full read/write benchmark, while the drive is empty. The problem is, the drive has a partition table, thus read/write will not proceed, and I can't figure out how to get rid of it.

So far as gparted and the disk utility can tell, it's all free, unallocated space at this time... though I had difficulty getting it to delete the swap partition. (I am doing this all from a CD boot, of course.) However, the read/write test still detects a partition table, and if I try to boot without the CD, I get a "no such partition" error and get thrown into grub rescue... so obviously, there's still something there.

How do I get rid of it?

EDIT: Okay, I jumped the gun posting this. In the disk utility, I formatted it with the "do not partition" option. That cleared it, and I now have a read/write benchmark test going. Sorry to clutter this with what was clearly a stupid question (nobody else had ever asked, so far as I could tell)... but I preserve this for posterity. :p

---

### Post by WorMzy on 2011-08-07
```
sudo dd if=/dev/zero of=/dev/sd# bs=512 count=1
```

Replace sd# with the disk identifier.

EDIT: I see you've solved your problem another way. :)

---

