---
title: "Help with First RAID"
date: 2010-03-17
forum: General Help
---

### Post by acroporas on 2010-03-17
I want to make a RAID5 array with 4 2TB hard drives.  One of the drives is full of data so I will need to start with a 3 disks and then once I copy the data from the 4th onto the array, I will then add the 4th drive.

This will be my first experience with RAID.  I've spent a few hours searching for info but most of what I have found is a bit over my head.

Can anyone point me to a good tutorial written for someone completely clueless?

---

### Post by prodigy_ on 2010-03-17
First thing that you absolutely need to do: **make a backup of everything valuable**!

Then, after you've connected your new HDDs, use ```
sudo fdisk -l
``` to check device names. Then come back here.

---

### Post by BrightEyesDavid on 2010-03-17
A couple of questions:

Do you wish to use Linux software RAID? Lots do and it comes highly recommended, as opposed to fake Motherbord RAID, which doesn't come highly recommended at all.

Do you want to perform an installation of Ubuntu during the RAID array making process? This is what I've done, and the Ubuntu alternate install disc comes with the capability to create software RAID arrays.

---

### Post by acroporas on 2010-03-17
> **BrightEyesDavid said:**
> A couple of questions:

Do you wish to use Linux software RAID? Lots do and it comes highly recommended, as opposed to fake Motherbord RAID, which doesn't come highly recommended at all.


Yes, was planning on a software RAID.  

> Do you want to perform an installation of Ubuntu during the RAID array making process? This is what I've done, and the Ubuntu alternate install disc comes with the capability to create software RAID arrays.

No, the RAID Array will only be used for data.  Ubuntu is already installed on an 80GB Intel x25M

---

### Post by acroporas on 2010-03-17
> **prodigy_ said:**
> First thing that you absolutely need to do: **make a backup of everything valuable**!


Are you saying this because I am likely to screw things up and loose all the data I put on the RAID in the first few weeks of being a noob and that I will need to keep the data backed up for a long time, or just pointing out that that all data on the drives will be wiped in the process of creating the array.

I know that all of the data on the drives will be lost during the creation of the array.  This is why it must start as a 3 drive array at first, because the 4th drive is full of data.

> 
Then, after you've connected your new HDDs, use ```
sudo fdisk -l
``` to check device names. Then come back here.

Can I address the drives by UUID or some other more reliable method than /dev/sd* ?  If you must use /dev/sd* how do you work around the problem of the letters changing every time you boot with an external storage device attached to the system?

---

### Post by prodigy_ on 2010-03-17
> **acroporas said:**
> Are you saying this because I am likely to screw things up and loose all the data
No it's just a usual warning, like "don't ever run a red light." Something people are likely to neglect and something they're likely to regret neglecting. ;-)

> **acroporas said:**
> Can I address the drives by UUID
UUIDs refer to partitions, not to physical devices.

BTW, a [HOWTO](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#RAID_5) with an example of a 3-disk RAID5/mdadm.

---

### Post by acroporas on 2010-03-17
> **prodigy_ said:**
> No it's just a usual warning, like "don't ever run a red light." Something people are likely to neglect and something they're likely to regret neglecting. ;-)

Ok, good.

> UUID referst to a partition, not to a physical device.

Ok, so there is no option other than to address the drives as /dev/sda, /dev/sdb, etc...

What happens when I boot with an external drive attached and the drive letters all change?  Will it just throw an error, or will it not realize anything is wrong and trash all of the data in the array?

Or is there a way other than uuid to force Ubuntu to allways give each physical drive the same letter.

---

### Post by prodigy_ on 2010-03-17
> **acroporas said:**
> What happens when I boot with an external drive attached and the drive letters all change?
Nothing bad, if the OS on your external drive supports Linux software raids. If you'll want to access your data you'll need to reassemble the RAID. Member disks are pre-partitioned and they contain information about what they are. But for mdadm you specify **/<device>/<partition number>**, not UUID.

---

### Post by acroporas on 2010-03-17
> **prodigy_ said:**
> Nothing bad, if the OS on your external drive supports Linux software raids. If you'll want to access your data you'll need to reassemble the RAID. Member disks are pre-partitioned and they contain information about what they are. But for mdadm you specify **/<device>/<partition number>**, not UUID.

Ok, well moving foward.  Here is the fdisk output you asked for.  

Just to be clear, there are currently only 2 of the 2TB drives attached at the moment.
```
~$ sudo fdisk -l


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9730    78150743+  ee  GPT

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000488db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003aef1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd4               1      121601   976760001   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ad9f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      243201  1953512001   83  Linux

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005a569

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001   83  Linux

```

---

### Post by prodigy_ on 2010-03-17
Normally, mdadm won't let you to create a RAID5 without at least 3 disks. The command format will be ```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/<????>
``` But of course you need to connect the 3-rd drive and change <????> to the name of the block device that represents this (currently missing) drive.

---

### Post by acroporas on 2010-03-17
> **prodigy_ said:**
> mdadm won't let you to create a RAID5 without at least 3 disks. The command format will be ```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/<????>
``` But of course you need to connect the 3-rd drive and change <????> to the name of the block device that represents this (currently missing) drive.

Thanks, that sounds pretty easy.  Yes I know, I'll have to wait until I get the final 2 drives installed in the system.  The other two drives won't arrive until tomorrow.../dev/sdb1 is actually the drive that will be added at a later point as it is the one with data still on it.  But I will not have any problems figuring out the /dev/sd? addresses of the 3 drives that I will be using.

So after than I just format /dev/md0, add /dev/md0 to fstab, and then reboot and it will be ready to use?

A few more questions.  Do I need to format the drives first, or will drives fresh out of the shrink-wrap be ready to go?

Also, just to ask one more time because this is a big concern of mine.

if for example, I set up the raid with the following command:
```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1
```
and then next time the system boots the letters have been shuffeled and the 3 drives that make up the raid are now /dev/sdc1, /dev/sdd1, and /dev/sde1 what will happen?  You said it would not cause data loss, but will ubuntu be able to find the drives and mount the array, or will it not work error until I get the system to boot with the three drives in the b,c, and d positions?

---

### Post by prodigy_ on 2010-03-17
For simplicity's sake, once you'll have connected all disks, use ```
df -h
``` command. Its output shows how much free/used space is on every partition. This way you'll easily identify the new disks (since they'll be empty).

---

