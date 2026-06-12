---
title: "UNR partitioner in installer says &quot;no root file system defined&quot;"
date: 2010-01-05
forum: General Help
---

### Post by hsartoris on 2010-01-05
I have no trouble getting the ISO onto a USB, or booting the OS. I hit install, and the installation steps go like this.
1. I select a language.
2. I select a keyboard.
3. I select a timezone.
(The above steps may be in a different order, I can't remember.)
4. I come to a screen that asks me whether I want to use the whole disk to install, or specify partitions manually. I select to specify manually, as I want to retain my other OS, Windows XP.
5. I select a partition that is already there and contains no files. I tell it to use as ntfs, and keep the original partition size. I cannot check the 'Format' box. I do not select to boot from DOS or Windows, as I have no idea what that means. I hit Forward. The following error message appears: Error: No root file system defined. I don't know what it means, nor how to fix it. I have previously tried to install Mint Linux, and gotten the same response. How can I fix this? :confused:

---

### Post by Cheesemill on 2010-01-05
You cannot install Ubuntu onto a NTFS partition, you need to use a different filesystem (ext4).
Ubuntu also needs a swap partition.

The easiest way to do this would be to boot back into Windows and use Disk Management to delete the partition you have set aside. Then restart the Ubuntu installation and select 'Use largest contiguous free space' when you get to the partitioning screen.

---

### Post by michy99 on 2010-01-05
The Ubuntu partition cannot be ntfs, It should be ext3 or ext4, and the mountpoint should be set to /

---

