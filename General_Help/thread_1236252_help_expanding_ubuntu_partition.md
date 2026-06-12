---
title: "help expanding ubuntu partition"
date: 2009-08-10
forum: General Help
---

### Post by callumacrae on 2009-08-10
Hello,

I'm not sure how partitions work, and I was wondering if anyone could help me?

I've filled up my Ubuntu partition (7.2gb). I apparently have a 40gb hard drive (according to my laptop spec) but in VParted it displays them as two devices, and I am unable to expand the Ubuntu partition. I don't actually want any partitions, as I don't use my laptop for anything but Ubuntu.

If anyone could help me I would be grateful,
~Callum

---

### Post by merlinus on 2009-08-10
Post results of

```
sudo fdisk -l
```

and if possible a screenshot of gparted.

---

### Post by callumacrae on 2009-08-10
> Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x294a294a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9375

I can't post a screenshot of GParted, but KDE Partition manager looks the same. The second partition used to have stuff in (from old setup) but I deleted it :)

---

### Post by zkriesse on 2009-08-10
when you load ubuntu it gives the option of the partition size.....

---

### Post by warp99 on 2009-08-10
The partitions with gparted are named /dev/hda or /dev/sda plus a number. If you had two devices they would be named hd0 and hd1. Most laptops do not have two hard drives, so I believe you may be reading the information incorrectly. Here's the help manual for gparted so you can check:

[http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html](http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html)

If you have one device then to grow the Ubuntu 7.2G partition you would first delete the second partition, then expand the Ubuntu partition to fill the empty space. Of course backup any data that you feel is critically before you begin.

---

### Post by callumacrae on 2009-08-10
I thought I was reading it wrong. They're called hda and hdb, as you can see in the screenshots.

I have read it, but I cant see how I would resize them.

~Callum

---

### Post by warp99 on 2009-08-10
Well you do have two devices and you're booting to the first one. You can copy the first partition to the second device, then run the grub boot manager to install grub on the second device. Here's a help guide on changing the disk that grub is running on:

[https://help.ubuntu.com/community/GrubHowto#Changing%20the%20Disk%20that%20Grub%20is%20installed%20to](https://help.ubuntu.com/community/GrubHowto#Changing%20the%20Disk%20that%20Grub%20is%20installed%20to)

After you install grub to the second drive you have to make changes to the /etc/fstab file on the second drive so that you're second drive's UUID is the root drive. 

And finally you need to make some changes to the file /boot/grub/menu.lst on the second drive so that drive's UUID also boots to the second drive. I can help you with these if you attach both the /etc/fstab file and the /boot/grub/menu.lst file off the second drive to your postings since it's kind of difficult.

After all this is done then you need to go into your computer's BIOS and change the boot drive from the first one to the second one. Good thing about this is if you mess up you can still boot off the first drive to see where you made any mistakes.

Edit:
You also don't need a swap partition with SSD unless you need to hibernate the computer.

---

