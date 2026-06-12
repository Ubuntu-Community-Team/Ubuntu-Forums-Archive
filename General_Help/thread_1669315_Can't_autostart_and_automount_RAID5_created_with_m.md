---
title: "Can't autostart and automount RAID5 created with mdadm but it starts manually"
date: 2011-01-17
forum: General Help
---

### Post by popacio on 2011-01-17
Relatively inexperienced user using Linux/ubuntu. Not too savvy I admit and like to use GUI as much as possible. Not a great fan of the Terminal window... ;)

I have installed a couple weeks ago Ubuntu 10.10 (Desktop Edition) using Alternative install disk (don't ask why!) on 4Gb usb stick. Working fine except one thing with the raid array...

I have created a _raid5 array made of 6 drives using GUI (Disk Utility)_. After an expansion of the array (or was it a reinstall of the OS, I can't remember exactly?) the array does not autostart anymore. Of course nor does it automount anymore...

THE WEIRD THING is that _I can still start it MANUALLY_ from the "Disk Utility" GUI after two tries. And it works just fine thereafter!!! _The first time i try to start it gives an error_ (something about /dev/md0_127 being not ready or buisy). _THE SECOND TRY ALWAYS WORKS_ like a charm, the array starts and i can mount it just fine.
Here is a screenshot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181339&stc=1&d=1295293139[/IMG]

I have also noticed that_ there is no entry in fstab for /dev/md0_ although I can manually mount it using the same Disk Utility GUI. That is strange to me. Is it normal? i could easily add it manually [FONT=Arial] but Ubuntu it won't boot anymore (i tried and failed, hence the reinstall).[/FONT]
I tried for two weeks to find a solution browsing on different forums but the problem is beyond my expertise...

BELOW are further details about my configuration mdadm.conf, fstab, fdisk -l result and other info. 
The matter is beyond my expertise and ANY HELP WOULD BE GREATELY APPRECIATED. I don=t want to loose my data but it would be nice to make this thing work and be able to access my fileserver via vnc instead of having to keep it connected to a lcd monitor as now.

This is the blkid result:
```

fileserver@fileserver:~$ sudo blkid
/dev/sda1: UUID="e11d8fab-63f5-4839-8734-7cd6e3ad5f16" TYPE="ext2" 
/dev/sda5: UUID="LdGhsH-DtaA-Ezld-IhSV-71yt-DnwM-mG2i1E" TYPE="LVM2_member" 
/dev/sdb1: UUID="29a9b4d2-c7be-f509-642b-671193826aa7" LABEL=":raid5_array" TYPE="linux_raid_member" 
/dev/sdc1: UUID="29a9b4d2-c7be-f509-642b-671193826aa7" LABEL=":raid5_array" TYPE="linux_raid_member" 
/dev/mapper/fileserver-root: UUID="50980294-38b3-4e75-a00e-6b2980756949" TYPE="ext4" 
/dev/mapper/fileserver-swap_1: UUID="77624bba-5a28-4ebd-a287-9504d04cea78" TYPE="swap" 
/dev/sdd1: UUID="29a9b4d2-c7be-f509-642b-671193826aa7" LABEL=":raid5_array" TYPE="linux_raid_member" 
/dev/sde1: UUID="29a9b4d2-c7be-f509-642b-671193826aa7" LABEL=":raid5_array" TYPE="linux_raid_member" 
/dev/sdf1: UUID="29a9b4d2-c7be-f509-642b-671193826aa7" LABEL=":raid5_array" TYPE="linux_raid_member" 
/dev/sdg1: UUID="29a9b4d2-c7be-f509-642b-671193826aa7" LABEL=":raid5_array" TYPE="linux_raid_member" 
/dev/md0: LABEL="raid5" UUID="8e69bf04-c8ca-4c32-8389-9d2231835456" TYPE="ext4" 
```here is my mdadm --detail --scan

```
fileserver@fileserver:~$ sudo mdadm --detail --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=6 metadata=01.02 name=:raid5_array UUID=29a9b4d2:c7bef509:642b6711:93826aa7
   devices=/dev/sdc1,/dev/sdb1,/dev/sdg1,/dev/sdf1,/dev/sde1,/dev/sdd1
```Here is my mdadm.conf content>
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/raid5 level=raid5 metadata=1.2 num-devices=6 UUID=29a9b4d2:c7bef509:642b6711:93826aa7 name=:raid5

# This file was auto-generated on Sat, 15 Jan 2011 16:29:32 +0200
# by mkconf $Id$
```This is my fstab (as i was saying /dev/md0 is missing):
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/fileserver-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e11d8fab-63f5-4839-8734-7cd6e3ad5f16 /boot           ext2    defaults        0       2
/dev/mapper/fileserver-swap_1 none            swap    sw              0       0
```And finally below is the fdisk -l result (notably the line **Disk /dev/md0 doesn't contain a valid partition table**):
```
fileserver@fileserver:~$ sudo fdisk -l

Disk /dev/sda: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000982c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          65      248832   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(31, 26, 59) logical=(64, 123, 54)
Partition 1 does not end on cylinder boundary.
/dev/sda2              66        1019     3663873    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(31, 59, 27) logical=(65, 32, 55)
Partition 2 has different physical/logical endings:
     phys=(487, 92, 53) logical=(1018, 50, 20)
Partition 2 does not end on cylinder boundary.
/dev/sda5              66        1019     3663872   8e  Linux LVM

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d7f59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc071

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/dm-0: 3477 MB, 3477078016 bytes
255 heads, 63 sectors/track, 422 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 218 MB, 218103808 bytes
255 heads, 63 sectors/track, 26 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d6967

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c1817

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d288

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003799e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      243201  1953512001   fd  Linux raid autodetect

**Disk /dev/md0: 10002.0 GB, 10001978490880 bytes**
2 heads, 4 sectors/track, -1853078016 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 2621440 bytes
Disk identifier: 0x00000000

**Disk /dev/md0 doesn't contain a valid partition table**

```Some help would be greatly appreciated. Thank you!

---

