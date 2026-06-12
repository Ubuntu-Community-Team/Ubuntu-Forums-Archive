---
title: "lilo not working to restore mbr"
date: 2011-07-03
forum: General Help
---

### Post by nieder on 2011-07-03
I have a Dell windows 7 laptop that suddenly is unable to boot: stops at a blinking cursor line after the Dell logo appears and is unresponsive (I can load the BIOS (F2) and the boot menu (F12) before the lock, but that's it).  Unfortunately, I don't have access to the Win7 install disc, so can't use Microsoft's recovery tool.

Following the advice of threads such as [this one]("http://ubuntuforums.org/showpost.php?p=8950739&postcount=7") and [this one]("http://ubuntuforums.org/showpost.php?p=6361212&postcount=4"), I loaded Ubuntu 11.04 with the Live/preview option from CD and tried running

```
sudo lilo -M /dev/sda mbr
```The command exited back to the Terminal prompt without any feedback (assuming it finished OK).  But when I rebooted the machine, I still got the blinking cursor.  Is there more to LILO  that I should do get the system booting correctly again?

So I tried to do more diagnosis to make sure there wasn't something more broken.

The HD seems ok.  Using Disk Utility, I can see that the HD (/dev/sda) is split into 3 partitions:

[LIST=1]
[*]DellUtility, 41MB FAT, /dev/sda1
[*]RECOVERY, 16GB NTFS, /dev/sda2
[*]OS, 304GB NTFS, /dev/sda3
[/LIST]
If I mount the partition "OS" via Disk Utility, I can navigate to the mount point, and open several files (PDFs but that shouldn't matter), so there doesn't seem to be any data loss.

```
ubuntu@ubuntu:~
$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5d633ed2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS
/dev/sda3        30801920   625140399   297169240    7  HPFS/NTFS

```I noticed that both fdisk and DiskUtility show that /dev/sda2 is the bootable partition.  Should /dev/sda3 (OS) be the partition that is bootable, rather than /dev/sda2 (RECOVERY)?

---

### Post by ladlers on 2011-07-03
You might need:
sudo lilo -M /dev/sda2 mbr
Another thing to try before that (just to see if it works) is to find the boot key on your computer (usually F8, F12, or ESC) and press it when you first turn on the computer. Then select your hard drive from the list to see if it boots.

---

### Post by Rubi1200 on 2011-07-03
ladlers,
your first suggestion won't work and may even make things worse. The whole point of installing lilo to the MBR is to be able to boot the operating system. Putting it on the partition will make things harder to fix.

The second suggestion is definitely worth trying.

---

### Post by nieder on 2011-07-03
Thank you both for your help. 

F12 brings up the boot options to choose between Internal HDD, CD/DVD/CD-RW Drive, onboard NIC, BIOS, and Diagnostics.  Selecting "Internal HDD" causes the white cursor, "CD/DVD" is how I get the Ubuntu Live CD to load, and "onboard NIC" brings up some text about the Yukon PXE.  BIOS brings up the BIOS (where everything looks OK), and Diagnostics brings up a test suite, that I've fully run w/ no errors reported.

F8 just makes it beep after any keypress.

ESC also causes beeping.  I've tried the other function keys with no effect.

F8 _should_ bring up the windows boot options (normal, safe mode, no network etc), but it doesn't look like Windows is even started at this low level.

Ubuntu's Disk Utility has an "edit partition" button that brings up a little  dialog that has a "bootable" checkmark.  Partition 3 (the main one) does  NOT have this set (fdisk -lu confirms).  Should it be set?

---

### Post by ladlers on 2011-07-05
I changed all of this so I guess you should reread it:

After:
 sudo lilo -M /dev/sda mbr
try:
sudo lilo -M /dev/sda
that may place the lilo program somewhere but it seems risky.

Lots of luck and sorry I didn't get back to you faster.

If you're not trying to install linux at all you might try the Dell recovery options perhaps selectable when first booting. Here is a summary from their website:
[http://support.dell.com/support/topics/global.aspx/support/kcs/document?c=us&l=en&s=gen&docid=DSN_362066&isLegacy=true](http://support.dell.com/support/topics/global.aspx/support/kcs/document?c=us&l=en&s=gen&docid=DSN_362066&isLegacy=true)
but I don't get what they mean by logging on with an administrative account. This action will delete all your user data. A better bet is to borrow a windows 7 install dvd from someone and boot it and follow its repair prompts. I don't have windows 7 so I couldn't help you further, but I know the Vista dvd which I have has repair options. You do lose all kind of windows repair/boot options when not having a windows loader.

---

### Post by aeiah on 2011-07-05
try using 'install-mbr' - its a linux command for putting a windows master boot record on the disk. worked for me to get rid of rootkits and the like. just running with the defaults should be fine. you should also make sure you have a 'bootable' flag set on the right partition. maybe it switched when things started going awry.

you could probably install grub using the super grub disk. it doesnt necessarily have to be the windows mbr - grub should be able to boot windows.

you could also consider copying all your data somewhere safe and using the dell recovery options. you might only be able to restore to factory defaults though.

---

### Post by ladlers on 2011-07-09
An update. You can legally download a windows 7 install disk from here:
[http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)
You have to burn it as an image, and viola, you have your windows 7 repair disk!
Also, because it is a file over 2 Gb, you may need a download manager program like this:
[http://www.freedownloadmanager.org/](http://www.freedownloadmanager.org/)
to download it. It will take long. Good luck.

---

