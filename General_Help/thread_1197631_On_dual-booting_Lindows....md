---
title: "On dual-booting Lindows..."
date: 2009-06-26
forum: General Help
---

### Post by ron3090 on 2009-06-26
Firstly, I finally got Windows installed as a dual boot on my computer as the slave 10gb HD to my 350gb (Or something like that) HD Xubuntu. Xubuntu can read the ntfs partition just fine, but windows cannot read Linux's etx3. I tried every tutorial I could find online, but nothing helped.
From what I could gather, it seems that my swap (or boot? Not sure) partition was first, and this caused problems.
Here is the output of fdisk -l:
> thomas@ubuntu-Sanyatu:~$ sudo fdisk -l

[COLOR="SeaGreen"]Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df1b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38820   311821618+  83  Linux
/dev/sda2           38821       38913      747022+   5  Extended
/dev/sda5           38821       38913      746991   82  Linux swap / Solaris
[/COLOR][COLOR="Blue"]
Disk /dev/sdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c25fa3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1215     9759456    7  HPFS/NTFS
[/COLOR]
Disk /dev/sdd: 507 MB, 507322880 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xd077a2b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         982      494809+   6  FAT16


The green is Linux, the blue Windows, and the black is just a USB drive I had plugged in.

And on a side note, how do I automatically mount the windows drive on startup? Also, how do I add it to the GRUB list, so I don't have to edit the BIOS at every startup?

---

### Post by ivanvajar on 2009-06-26
Windows can't see ext3 by default. There is software for Win to do that, but you'll have to google a bit since I forgot what program it is.

> sudo gedit /boot/grub/menu.lst

and post it here to solve that BIOS changing. You need to add few lines to menu.lst to make your Win bootable with GRUB. You need to add

> title		Windows 95/98/NT/2000
root		(hd1,0)
makeactive
chainloader	+1

after > ### END DEBIAN AUTOMAGIC KERNELS LIST so Win will be bootable via GRUB after kernel updates

---

### Post by ron3090 on 2009-06-26
I tried all of that software, none of it works. As stated, I think it is because I have the boot partition first.

EDIT: Also, what do you mean by, "after kernel updates?"

---

### Post by ron3090 on 2009-06-26
Okay, I inserted the line as you said, and now GRUB hangs on the words "Starting up..."

Once again leaning towards the Windows problem, is there a way to put the etx3 partition first, without formatting the drive, and without affecting the boot?

---

