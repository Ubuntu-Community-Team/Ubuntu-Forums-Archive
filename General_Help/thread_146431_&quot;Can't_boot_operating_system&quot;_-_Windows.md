---
title: "&quot;Can't boot operating system&quot; - Windows"
date: 2006-03-18
forum: General Help
---

### Post by drobvice on 2006-03-18
I have 1 hard drive, hda, with 2 partitions, hda1 and hda5.  Both of these are (were) NTFS.  Hda1 is Win XP and hda5 was a for media.  When I installed ubuntu, I used the guided partitioning (ubuntu 5.1) and I wanted to use roughly half of the th 36 gb media drive on hda5 for ubuntu.  I installed grub to a floppy and did not touch the MBR.  Now when I boot, I get a message of "Can't boot operating system when I try to go into windows.  I am not able to mount the Windows partition in ubuntu, but that may be my fault.  I rebooted with a live kanotix cd and it mounts hda1 and I can explore the drive fine.  If I use grub on the floppy, I can boot up windows.  If I run "sudo fdisk -l", I get this:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        7706    20940727+   f  W95 Ext'd (LBA)
/dev/hda3   *        7707        9729    16249747+  83  Linux
/dev/hda5            5100        7616    20217771    7  HPFS/NTFS
/dev/hda6            7617        7706      722893+  82  Linux swap / Solaris


I remember looking at this when I was in windows and there were 2 primary partitions (XP and Ubuntu) and hda3 was listed after hda6.  Also, the swap partition was listed in the same "container" as the remaining 15 gb of my 2nd NTFS partition.  Now that I look at it this "container" is listed as W95 Ext'd (LBA).  Is this what's keeping me from booting?  If so, how can I fix it?

---

### Post by Lunixfanboy on 2006-03-18
Your output of fdisk indicates that /dev/hda3 is marked as the bootable partition, while Windows would have to be for Windows to boot (/dev/hda1). The asterisk next to /dev/hda3 is the bootable indicator. So, if you can still access using fdisk in some fashion, run it again without any options (i.e. fdisk without -l) and use m for help, which will get you the -a option to toggle bootable. Set /dev/hda1 as bootable, and you should be able to boot Windows again.

---

### Post by drobvice on 2006-03-18
You are great!  I booted into windows and blew away the rest of the disk.  It was set up way too strangely for me and will probably reinstall ubuntu to the entire rest of the disk.  I had to experiment with the fidisk command and finally saw the option to write the table but was afraid to do so.  Before your reply and after I deleted the rest of the partitions, I tried recovery console on XP and and did FIXMBR and it didn't work but I have now experienced that as well.  Just want to say thanks again!

---

### Post by Lunixfanboy on 2006-03-18
I am glad I could assist you.

---

