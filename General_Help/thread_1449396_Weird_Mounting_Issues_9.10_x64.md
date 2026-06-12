---
title: "Weird Mounting Issues 9.10 x64"
date: 2010-04-07
forum: General Help
---

### Post by gotmonkey on 2010-04-07
I am running into something weird. I had to reload my fileserver because the O/S drive died (Ubuntu 9.04 with SMP kernel). I have a 3Ware 9650SE 8-port card in the system. When I reloaded the system, I decided to give 9.10 x64 karmic a try. 

When the system boots, the drives labeled "media" and "adult" mount just fine, but the "storage" drive does not mount.

When I try to mount the drive, it returns this: 
Error mounting: mount exited with exit code 1: helper failed with: mount: only root can mount

and it tells me that /dev/sdb1 is either unmounted or busy.

What I did find is that if I delete the /media/storage directory I created for mounting and commented out the line for "storage" in my fstab, it would allow me to mount the drive using nautilus and providing a password. It would mount the drive as /media/storage

Has anyone seen this problem before and has any idea how to resolve? My next move is to downgrade back to 9.04, where it was working just fine. 

$ uname -a
Linux fileserver 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64 GNU/Linux

Drive layout
1x250GB Drive on motherboard controller for OS
4x500GB RAID-10 on 9650SE: 1TB ext3 partition
4x1TB RAID-5 on 9650SE: 2TB and 734GB partitions

I used blkid to get the UUID for each drive to add to the fstab to mount at boot. 
> 
 sudo blkid
/dev/sda1: UUID="9971c591-4d90-4dec-bced-a6c8511ce730" TYPE="ext4" 
/dev/sda5: UUID="6bec6435-d0c7-457c-9516-e18524d6bf96" TYPE="swap" 
/dev/sdb1: LABEL="storage" UUID="33dde6b0-ba49-4125-8618-2c73fbd1c3cd" TYPE="ext3" 
/dev/sdc1: LABEL="media" UUID="65c52094-be18-46c5-bf82-095e5f01eb10" TYPE="ext3" 
/dev/sdc2: LABEL="adult" UUID="8efb4fbd-8c5c-4bc4-a6a7-cda97faed0da" TYPE="ext3" 




Here is the output of $sudo fdisk -l
> 
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x178b7784

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 1000.0 GB, 999978696704 bytes
255 heads, 63 sectors/track, 121573 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008ff4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121573   976535091   83  Linux

WARNING: The size of this disk is 3.0 TB (2999967547392 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID 
partition table format (GPT).


Disk /dev/sdc: 3000.0 GB, 2999967547392 bytes
255 heads, 63 sectors/track, 364725 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002da17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      267349  2147480811   83  Linux
/dev/sdc2          267350      364725   782172720   83  Linux


> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9971c591-4d90-4dec-bced-a6c8511ce730 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6bec6435-d0c7-457c-9516-e18524d6bf96 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


#Storage
UUID=33dde6b0-ba49-4125-8618-2c73fbd1c3cd /media/files	ext3	defaults 0 1
#Adult
UUID=8efb4fbd-8c5c-4bc4-a6a7-cda97faed0da /media/adult		ext3	defaults 0 1
#Media
UUID=65c52094-be18-46c5-bf82-095e5f01eb10 /media/media		ext3	defaults 0 1


---

### Post by dcstar on 2010-04-07
> **gotmonkey said:**
> 
........
What I did find is that if I delete the /media/storage directory I created for mounting and commented out the line for "storage" in my fstab, it would allow me to mount the drive using nautilus and providing a password. It would mount the drive as /media/storage
........

Do not touch the /media folder, that is a system folder for the purposes of automatically mounting removable storage devices.

If you want to mount anything using fstab then create mount points outside of any system folder.

---

### Post by gotmonkey on 2010-04-07
I wasn't deleting the system folder /media. What I had deleted was a subfolder that I created. I had done the same type of setup in prior versions of ubuntu with no issue.

I can give creating different mount points a try

Thanks

---

### Post by gotmonkey on 2010-04-07
Trying to create a mountpoint outside of system folder came up with the same result.

---

