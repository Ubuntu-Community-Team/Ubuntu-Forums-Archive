---
title: "software RAID1 setup"
date: 2010-11-14
forum: General Help
---

### Post by salvo84 on 2010-11-14
I am trying to setup a software RAID1 using mdadm.

My setup:
Ubuntu Desktop 10.10 on a 8Gb SDD
2 x 2TB WD20EARS

I was using one of the 2TB drives in a windows system as a data drive (NTFS). 

I formated the fresh drive using fdisk and the various guides on how to do it properly for the 4k sector size. It has a ext4 partition using the entire drive. 

Installed the NTFS drive in the Ubuntu system and am currently copying the files from the NTFS to the ext4 drive.

The plan is, once the copying is finished, to align and format the NTFS drive to ext4 and then setup a software RAID1 using the 2 drives.

I've seen some guides on setting up RAID but from what it seems I would have to format the drives again in order to get it to work. I don't want to do that since I would loose my data.

Is it possible for me to setup RAID1 without loosing my data?

---

### Post by salvo84 on 2010-11-14
found a good guide [here]("https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID") that I am going to attempt to follow. I'll post updates once I figure it all out.

---

### Post by salvo84 on 2012-02-28
Turns out the guide I posted was exactly what I wanted to do, and it worked great. (I only did the steps that applied for my situation)

From the guide: > Create a single-disk RAID-1 array with our new disk
Move all your data from the old-disk to the new RAID-1 array
Verify the data move was successful
Wipe the old disk and add it to the new RAID-1 array

Finally getting around to posting, but the RAID has been running great for over a year now.

Recently I moved back to 10.04 LTS because of issues configuring a TAP with a bond setup for OpenVPN in 10.10.

While installing 10.04 I decided to configure block encryption using LUKS/dm-crypt on the RAID. I am currently in the process of using badblocks to check both disks and write pseudo random data to the drive. I plan on starting a new thread with what I accomplished. I'll add the link here once I start it.

---

