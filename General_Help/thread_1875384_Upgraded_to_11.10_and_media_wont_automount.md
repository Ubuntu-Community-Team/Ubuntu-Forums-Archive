---
title: "Upgraded to 11.10 and /media wont automount"
date: 2011-11-04
forum: General Help
---

### Post by RedEyeZ88 on 2011-11-04
Alright,

So I have been researching some methods to help recover my problem, but have yet to have any success.

I have built an Ubuntu 11.04 RAID server using MDADM and Netatalk in order to AFP. Everything worked fine, and I created an ext4 partition scheme with my original set up. 

A few weeks ago, I updated to Ubuntu 11.10, and was experiencing some glitches in my system, but the RAID worked just as previously configured. I then decided to reformat/reinstall Ubuntu on the OS drive (Not part of the RAID 6), in order to help alleviate some glitches. 

Installation went smoothly, and after installing MDADM, I can go into Home, and mount Ubuntu-NAS (my RAID). 

My issue is that I would like the RAID to mount upon boot, just as it used to. When attempting to edit my fstab in order to, I receive an error message in "fdisk-l", stating: "/dev/md127 doesn't contain a valid partition table."

I have yet to figure out how to fix this problem. The data is all intact, and everything works fine only after I mount the drive. Please help! I have posted on ask ubuntu, and I have done a few days of searching but still now luck. Ill post my fdisk -l:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   156299374    78149687   ee  GPT

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000412f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005cf54

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a563b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088e1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a104e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000271fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/md127: 10002.0 GB, 10001973248000 bytes
2 heads, 4 sectors/track, -1853079296 cylinders, total 19535104000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 1048576 bytes / 5242880 bytes
Disk identifier: 0x00000000

Disk /dev/md127 doesn't contain a valid partition table

---

### Post by jnorthr on 2011-11-04
if you can open a console terminal and type this command:
cat /etc/fstab

you will be able to see the parameter values used to auto mount drives. I am not a guru on this so you will need to do a bit more research on how to get your raid to auto mount. I believe it requires the word 'auto' in the line but that's just a guess. sorry.

---

