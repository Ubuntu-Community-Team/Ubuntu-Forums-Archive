---
title: "file to big to send?"
date: 2011-04-19
forum: General Help
---

### Post by Arminius on 2011-04-19
I have a 9.4GB file, and half way through transferring to a removable hard drive it says file to big.
are there options?
some good sync programs that can do it?

---

### Post by plucky on 2011-04-19
> **Arminius said:**
> I have a 9.4GB file, and half way through transferring to a removable hard drive it says file to big.
are there options?
some good sync programs that can do it?

What is the format on the external drive? Could it be Fat32.
That has a 4GB file size limit.

Change the format to NTFS if you need it compatible with windows.

Good Luck

---

### Post by Arminius on 2011-04-19
yeah it's fat32?
ummmm it doesn't need to be compatible with windows, so is NTFS the only option?

---

### Post by 3rdalbum on 2011-04-19
If you're transferring big files from Linux-to-Linux, then format your drive as Ext3 or Ext4; it'll be much MUCH quicker than NTFS.

If it has to go through Mac OS or Windows though, NTFS will be your only option really, unless you installed an Ext3 driver on the Windows/Mac system.

---

### Post by Arminius on 2011-04-19
which should I go for? ext3 or ext4?
I heard that ext4 was faster but your more likely to lose data?

---

### Post by Grenage on 2011-04-19
I'd use EXT4; it has various improvements over EXT3, and it's rather stable.  Two years ago I would have said EXT3, but not now.

---

### Post by yetiman64 on 2011-04-19
OP, I must agree with both Grenage and 3rdalbum about using ext4. 3 of my 4 storage partitions are ext4 the other is ext3 (a relic from my Jaunty install days). ext4 is both stable, and very fast compared to NTFS (which I now no longer use - as Vista is dead and gone from here).

If you don't need to access files from Windows or Mac, ext4 is my recommendation also.

---

