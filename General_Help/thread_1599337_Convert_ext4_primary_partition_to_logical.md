---
title: "Convert ext4 primary partition to logical"
date: 2010-10-17
forum: General Help
---

### Post by fri.K on 2010-10-17
Hello
I'm trying to convert big ext4 partition to logical. I was able to do that with Arconis Disk Director Home 11 with swap and ext3 partition, but it doesn't recognize ext4.

Unfortunately I can't copy 2TB data to another HD :(
Now I have:
Pri   /boot     ext3   
Log   /         ext3
Log   swap      swap
Pri   /media/X  ext4    <- 2TB

When I do that I be able to install Ubuntu Server next to CentOS. And I will add partition /home(ext4) for both and "/"(ext4) for Ubuntu.

Sorry for bad english.

---

### Post by srs5694 on 2010-10-18
If I understand correctly, you want to add two new partitions, presumably after the current ext4 partition. If this is incorrect, please elaborate on what you want to do, and post the output of "sudo fdisk -lu" on the system, ideally between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

If this is a Linux-only disk, you could convert it from Master Boot Record (MBR) form to GUID Partition Table (GPT) form. GPT supports up to 128 partitions by default, and it doesn't have a primary/extended/logical partition distinction, so you could easily resize (if necessary) the ext4 partition and create as many partitions after it as you like. Use [GPT fdisk](http://www.rodsbooks.com/gdisk/) to do the conversion non-destructively. You'll need to re-install your boot loader after you do the conversion. If you're using GRUB 2, you'll benefit by creating a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) (GPT fdisk type code EF02; it can be tiny -- as small as about 35 KiB) before you re-install GRUB.

---

### Post by zazuzimbo on 2010-10-18
I don't know how to convert the partition. But it might not be needed.

You have enough free space to create the new partitions you want, right?

I think gparted would be able to resize your 2TB partition (preserving contents). Try it. You'll end up with free space that can be used for the new partitions appropriately.

Tell us what happens. :)

---

### Post by srs5694 on 2010-10-18
If resizing the ext4 partition, be cautious. Taking space from the end of the partition is likely to take little time and be relatively safe; but taking space from the start of the partition is likely to take much more time and be much less safe. If other partitions, such as the logical ext3 partition, can be resized for at least some of the required space, then creating the two new partitions might be easier.

---

