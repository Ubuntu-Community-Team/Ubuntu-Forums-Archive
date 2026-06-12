---
title: "Installation and partitions"
date: 2011-04-03
forum: General Help
---

### Post by Archie Moses on 2011-04-03
Sorry, I know this question gets repeated over and over, but every scenario seems different.

Brand new HP Compaq Presario CQ56, want to dual-boot 7 & Ubuntu.  Too many partitions I think;

HD0 - 298.09 GB

System 
199 MB NTFS

C:
279.36 GB NTFS

RECOVERY D:
18.43 GB NTFS

HP TOOLS
103 MB FAT32

Want to add Ubuntu + Swap in the 90 or so GB range, fairly new to partitioning.  Trying to create recovery disks using system tools is over 16 Gb, for that kind of expense I may as well just order recovery disks OEM if (When) Windows falls apart.

Thinking about just nuking HP TOOLS & Shrinking C:, but wondering if there is a better way?

Thanks!

---

### Post by techunit on 2011-04-03
I apologize for the repetition in saying what set your at but I am trying to make sure you don't mess up.

The harddisk can only have 4 primary partitions. You already have 4 primary partitions so one has to go. Kill HP-Tools would work. Ubuntu itself creates 2 partitions so. Lets do this right.

IN WINDOWS. IN WINDOWS. do get that this step happens in WINDOWS. Good

Shrinking a Windows 7 partition should be done in Windows. Use this guide
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Using windows partitioner you can also remove the HP tools.

Now that you have removed HP tools and have made room for Ubuntu you can boot from your live cd.

IN THE LIVE CD IN THE LIVE CD. This step happens in the live cd. Got it good.

Open Gparted and create a new partition in the space you freed up. It should be an extended partition. click apply and save the changes to the disk.

Once completed right click on the extended partition and create a partition inside of it. Should it should be ext4 and about the size of the extended partition minus the amount of ram you have.

Create another partion inside the extended partition this should be set as swap. It should be the remainder of your space and about the size of your ram.

Now in the installation choose manual parition and mark the ext4 partition as the one you'd like to format and set the boot point to "/"

Swap should be formated as well.

Make sure that GRUB is set to sda and nothing but it.

---

