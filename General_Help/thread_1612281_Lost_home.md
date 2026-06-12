---
title: "Lost /home"
date: 2010-11-03
forum: General Help
---

### Post by NeverSage on 2010-11-03
Hey guys,

I think through my ignorance I may have just permanently lost my /home directory, but I was hoping some intelligent soul here could help me get it back.

I have /home on a separate partition.  I had an old partition I wanted to get rid of.  I used gparted from a liveCD and deleted the old partition which was at the front of the drive.  I wanted to give the extra space to /home so I expanded /home to the front of my hdd.  Upon rebooting I realized grub was gone.  I was able to install grub onto the correct partition.  But now when I boot I get the Ubuntu logo with "The disk drive for /home is not ready yet or not present".  I can skip mounting or do manual recovery.  After skipping I opened gparted with terminal and got "invalid partition table on /dev/sda -- wrong signature 820".  In gparted everything is shown as unallocated.  By doing fdisk -l I get:
```
Warning: invalid flag 0x0820 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000131d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1      109444   879103208+   5  Extended
/dev/sda3          109444      121602    97657856   83  Linux

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6d79

```fstab says:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d1682e22-d4a2-4621-be55-098978d1119c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=b519bd76-02d3-4618-94a0-9d0ee76f39f2 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=1e0b64d2-82f3-445b-9220-22813b7b15fc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Any ideas?  I'm stumped at this point.  There are a couple threads I found that look promising but they don't address my specific problem and I'm worried of doing more damage...

Thanks guys!

---

### Post by Quackers on 2010-11-03
Did Gparted take a long time to run the changes?
Try booting normally and just leave the error message there for a minute or two, if you haven't already tried that.
It doesn't sound too good though. I don't suppose you made a backup of /home?
Another option may be to try using testdisk (which I think is on the live cd, if not you can install it from Synaptic) to recover the /home partition. Definitely worth a try.
Good luck.

---

### Post by NeverSage on 2010-11-03
Thanks for the reply Quackers.  Gparted did indeed take a long time.  Over 5 hours.  I guess I shouldn't have been messing around with stuff I didn't understand.

BUT

I was able to fix my problem by downloading and using TestDisk from my LiveUSB!  It was surprisingly easy with that :)

---

### Post by Quackers on 2010-11-03
Aha! Excellent! Well done :-)

---

