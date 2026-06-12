---
title: "2nd RAID 0 array"
date: 2011-05-12
forum: General Help
---

### Post by elliotbeken on 2011-05-12
Hi all,

i have ubuntu 10.10 64bit install on 2x 500gb hard drives and all works fine however i have two more 250gb hard drives that i have put in a different raid 0 array and when i try to create a partition using the disk utility i get this error message.

> Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/dm-0, start=0, size=499994853376, type=0x83
Entering MS-DOS parser (offset=0, size=499994853376)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 499990063104, type 0x83)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
new partition
added partition start=512 size=31744
committed to disk
Error doing BLKPG ioctl with BLKPG_ADD_PARTITION for partition 2 of size 512 at offset 31744 on /dev/dm-0: Invalid argument


how do i fix this ?

---

### Post by elliotbeken on 2011-05-12
i have also tried gparted live CD with no luck

---

### Post by elliotbeken on 2011-05-13
I have fixed the problem doing the following:

run this command on the drives in the broken array

> sudo dmraid -rEI then went in to the RAID menu (just after bios) and deleted the array then re-made it.

after this i booted up ubuntu again and used the disk utility to create a partition on the raid.

hope this helps....

---

### Post by mercury80 on 2011-06-22
I think there is something wrong with dmraid. If you investigate i think you will realize that there is actually no path called: /dev/dm-0

---

### Post by kaicrr77 on 2011-07-03
I ran into this today with my HTPC which is using NVRAID.
I originally had 2 drives mirrored which Ubuntu didn't have a problem with... during the install. Later I wanted to add secondary storage so I figured I would use the Disk Utility. Obviously I got the "error doing with BLKPG" i dropped and recreated the RAID collection many times which didn't work.

Then i decided to do the entire creation via command line and was able to pull it off. I basically used bits and pieces of this: [http://en.gentoo-wiki.com/wiki/RAID/NVRAID_with_dmraid]("http://en.gentoo-wiki.com/wiki/RAID/NVRAID_with_dmraid")

1. ```
sudo dmraid -rE
``` to remove the old raid metadata
2. ```
sudo reboot
```Reboot. After the BIOS recreate your Raid collection within the onboard RAID disk utility.
3. ```
sudo dmraid -r
``` to look at what drives are involved in the raid collection. Copy the part that says nvidia_xxxxxx" which correlates to your drives.
4.```
sudo fdisk /dev/mapper/nvidia_xxxxx
```create your partition 
5.```
sudo reboot
```Reboot
6.```
sudo mkfs.ext4 /dev/mapper/nvidia_xxxxx
``` create your file system...and your done. Now it appears within the Disk Utility like the others and you can mount it.

---

