---
title: "Possible to increase size of hfs+ partition?"
date: 2010-04-22
forum: General Help
---

### Post by themusicalduck on 2010-04-22
I have an hfs+ partition on a drive with a few other partitions. I deleted the partition to the right of it and wanted to expand it into the space, but it just won't do it. It will let me shrink the partition but not expand it.

I installed any programs that looked relevant to hfs (I think I installed hfsutils and hfsplus), but it didn't help.

I'm using gparted on a 10.04 live disc.

---

### Post by themusicalduck on 2010-04-23
bump

---

### Post by louieb on 2010-04-23
According to [http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php) . Gparted can't grow an hfs formated partition.  Guess your stuck looking to Apple software for a solution.

---

### Post by themusicalduck on 2010-04-23
Thanks for the info.

The problem is, how can I run OS X software that will partition the drive without booting into OS X and thus mounting it? It doesn't seem like you can get a live OS X disc (without a fair bit of hacking anyway).

---

### Post by srs5694 on 2010-04-23
Try using your OS X installation disc. You should get to a point where the menu bar appears at the top of the screen. From that you can select Disk Utility, which should then enable you to resize your HFS+ partitions. This will only work on GUID Partition Table (GPT) disks, though, and I believe there must be some free space after the partition in question. Post more details about your partition layout if these conditions aren't met; there may be workarounds.

---

### Post by themusicalduck on 2010-04-24
I actually had a try at what you suggested already. For some reason the disk utility wouldn't let me resize it. The only option I could find that looked like resizing was a button called "Resize image" but it was greyed out. I did unmount the partition first as well. I couldn't see any other option for resizing it.

According to gparted my partition table is "msdos" and not GUID like you said. Might that be the problem?

This is how the partitions are set up.

---

### Post by srs5694 on 2010-04-24
Yes, Disk Utility will only resize GPT disks, not MBR ("msdos" to GParted) disks. Is the NTFS partition a Windows boot partition? If not, and if the system either doesn't have a Windows installation or you've got Windows Vista or 7 installed on another disk, you should be able to convert to GPT using [GPT fdisk.](http://www.rodsbooks.com/gdisk/) Be sure to read my [Converting to or from GPT](http://nessus.rodsbooks.com/gdisk/mbr2gpt.html) page, and be aware you may have to re-install your boot loader.

If you're booting Windows from the disk, you can still convert to GPT and resize the HFS+ partition, but then you'll need to either create a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) or convert back to MBR to make Windows happy. Again, boot loader issues may crop up.

Alternatively, and perhaps more safely, you could back up the contents of the HFS+ partition, delete it, create a new partition in the blank space, and restore the contents to the new partition. This will probably take more time, but it could take less time than it would if you run into boot problems because of an MBR-to-GPT conversion.

---

### Post by themusicalduck on 2010-04-25
Thanks again!

In the end I used Carbon Copy Cloner to copy the partition onto a bigger partition. Reinstalled Chameleon (not sure if that was even necessary), then reinstalled grub, deleted the old partition and now everything works swimmingly.

---

