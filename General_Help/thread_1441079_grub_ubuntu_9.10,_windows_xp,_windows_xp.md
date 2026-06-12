---
title: "grub: ubuntu 9.10, windows xp, windows xp"
date: 2010-03-28
forum: General Help
---

### Post by rockette morton on 2010-03-28
Hi!

Before I installed ubuntu I had my PC set up to dual boot two seperate windows xp installations.  Now, if I want to boot into windows, I have to select the XP boot manager in grub, and then make another selection from there.  Can I edit grub to handle everything, rather than selecting another boot manager? Also, Grub is starting to get a little cluttered so I was wondering if I could edit/comment out any older/redundant versions of Ubuntu.

I have googled this many times but I came to understand that although this may be possible, it will depend on many variables and so I'd really appreciate some help with this!

Here is how my hdds are set out:

255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xddeeddee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433        9729    58613152+   f  W95 Ext'd (LBA)
/dev/sda5            2433        7296    39070048+   7  HPFS/NTFS
/dev/sda6            7297        7305       72261    7  HPFS/NTFS
/dev/sda7   *        7306        7331      204799+  82  Linux swap / Solaris
/dev/sda8            7332        9729    19261903+  83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc954a6f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   42  SFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x032bd35d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24792   199141708+  42  SFS

Do let me know if there's anything else that you need to know.  

Many, many thanks,
Tim

---

### Post by oldfred on 2010-03-28
Because your second windows is in an extended partition it is more difficult but not impossible. Only a couple of very knowledgeable members of the forum seem to know how to do this and I will give you links to where they helped others do this.

Info on how windows boots multiple versions. IF you had primary partitions and was reinstalling this would work:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)


Way to boot windows in extended logical partition with lilo's MBR
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)

I do not understand why you do not have a boot flag on the windows partition but  I believe grub does not need it. I would move the boot flag to your windows primary partition using gparted or command line.
set boot flag on for sda1 (off for others)
sudo sfdisk -A1 /dev/sda

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)


In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
Be sure not to delete the one you are using or you will not be able to reboot.

---

### Post by rockette morton on 2010-03-28
hi! thank you so much for finding these for me.  i have already tidied up grub so many thanks for that link.  the others may take some time to work through, and since i'm getting some new drives next week i may consider a reinstall and work from there.  i will let you know how i get on.  thanks once again!

Tim

---

