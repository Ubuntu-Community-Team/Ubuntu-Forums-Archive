---
title: "Turning bootable partition into an ISO?"
date: 2009-07-26
forum: General Help
---

### Post by bchurchill on 2009-07-26
Short Version:
How do I take a bootable partition mounted on my system and make a bootable ISO file that I can burn onto a DVD or USB flash memory drive?

Long version: 
I've been running Ubuntu 9.04 for a while now.  Previously I had windows installed, and when I installed Ubuntu I chose not to override a backup partition to restore Windows.  I'm getting a new computer and want to setup a dual-boot using my current backup partition to install windows (wine just doesn't cut it sometimes...).  So now I'm trying to make an ISO that I can use to make a startup disk.  I have the device (/dev/sda2) and mounted it (/media/disk).  It's a FAT32.  But I'm not sure how I should do this, and in particular, how to make sure that I can boot using it.

I've searched around for a while, but I can't find any comprehensive description on how this will work.  Any hints on where to look?

Thanks in advance.

---

### Post by bchurchill on 2009-07-26
I've found a good-looking open source program called ISO Master that allows one to build an ISO and create a boot record.  Now I need to find the boot sector of my partition, which *should* be easy since it's located on the first sector of it; however I don't know how to look at the first sector of the volume, or find the file containing it.  Any suggestions?

I've already tried

```
$find . -size 512c -print
```to locate the appropriate file, but couldn't find any that were boot sectors (checking last two bytes).  The only file that seems like it may be helpful is a 1024b file called bootfix.bin which seems to contain executable code containing a boot sector, but I don't think this is what I want.

I'm still learning about how all this works, so any help would be greatly appreciated!

---

