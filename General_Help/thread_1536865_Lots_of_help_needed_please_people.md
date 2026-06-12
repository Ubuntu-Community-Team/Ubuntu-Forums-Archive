---
title: "Lots of help needed please people"
date: 2010-07-22
forum: General Help
---

### Post by hullpaul on 2010-07-22
Hi just got hold of a sony vaio vgn-ar730e and like any sensible person i have put ubuntu on it (clean install) my old laptop a dell insipron work perfectly straight away well this one i have some problems please help
1)i have 2 hard drives (not partitions) 250g main one and a 160gig hard drive  ata st9160821as i was planning to use as mass storage but it dont show up on the system to be able to do this i can see it on the disk utility but cant access it.

2)i cant get the installed blueray drive to burn it will read but not burn its a matshita bd-cmb uj-120 

3) because of number 2 i brought a external dvdrw (dvd drive tsstcorp cd/dvdw ts-l532a)  it will read but if i put blank disk in it goes missing no drive nothing only on disk utility can i see it also if i cant sort out number 2 how to i make it primary drive if i can get it to burn?

4)need drivers for a  logitech c250 webcam will work on cheese  but not amsn 

all help would be gratefully received

all the best

Paul

---

### Post by no2498 on 2010-07-23
? just asking do you have the jumpers set right master an slave
and look in the usb

---

### Post by patchwork on 2010-07-23
> 1)i have 2 hard drives (not partitions) 250g main one and a 160gig hard  drive  ata st9160821as i was planning to use as mass storage but it dont  show up on the system to be able to do this i can see it on the disk  utility but cant access it.

Can you please post the output of ```
sudo fdisk -l
```?  This will list the drives and partitions with their device names, so that you can either 

1). Manually mount the drive whenever you want to access it
2). Add the drive to your /etc/fstab for automounting the drive on boot

Whichever you'd like to do, we can assist you in completing.

---

### Post by hullpaul on 2010-07-24
output to the post

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c2334

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29273   235129856   83  Linux
/dev/sda2           29273       30402     9066497    5  Extended
/dev/sda5           29273       30402     9066496   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b076f

   Device Boot      Start         End      Blocks   Id  System



and if ican id like it to auto mount thanks for your help

---

### Post by patchwork on 2010-07-24
> Device Boot      Start         End      Blocks   Id  System


Did you cut-off your output for /dev/sdb?  If the drive is partitioned, the device information should show (similar to the /dev/sda output:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29273   235129856   83  Linux
/dev/sda2           29273       30402     9066497    5  Extended
/dev/sda5           29273       30402     9066496   82  Linux swap / Solaris

)

This information would have the identifier and filesystem type for the partition on the 160GB drive you'd like to use as mass storage, and we will need this information to add to your /etc/fstab



To ensure that the drive is not currently in your /etc/fstab, can you also post the output of ```
cat /etc/fstab
```?

---

### Post by hullpaul on 2010-07-25
this is all off the the 1st thing you asked me to copy-

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c2334

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29273   235129856   83  Linux
/dev/sda2           29273       30402     9066497    5  Extended
/dev/sda5           29273       30402     9066496   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b076f

   Device Boot      Start         End      Blocks   Id  System
 

and here is the 2nd


paul@paul-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1bca07b3-fe2d-4acd-afbb-343019f5d6d8 none            swap    sw              0       0


hope this makes sense

---

### Post by patchwork on 2010-07-25
Have you already formatted the 160GB drive?  If so, there should be a filesystem on it (right now it doesn't appear that there is).

---

### Post by hullpaul on 2010-07-25
i formatted it while using windows before i put ubuntu on now the only way i know its there is it shows up on disk utility donsnt show on computer atall

---

### Post by patchwork on 2010-07-25
Well, there doesn't appear to be any partitions or filesystem on the drive, so that is the first issue to tackle.  Using gparted, you will need to partition the drive and create the filesystem.  Popular filesystems include:

ext4, ext3 for linux data only
fat for linux and windows data

You can obviously create more than one partition, if you choose.  Once this is done, running the sudo fdisk -l command should return the partition information for /dev/sdb

We will then use this information to add to your /etc/fstab

---

### Post by hullpaul on 2010-08-26
thank you got it sorted now, please help with my tsstcorp cd dvdw ts-l532a when i connect to pc it shows up i can even play dvds but if i put a blank one in to burn anything the whole drive goes missing (still shows on disk utility) so i cant burn anything
please help
Paul

---

### Post by TwoEars on 2010-08-26
This sounds like a hardware related problem. After googling, I found this [http://club.myce.com/f105/problems-tsstcorpcd-dvdw-ts-l532a-189916/](http://club.myce.com/f105/problems-tsstcorpcd-dvdw-ts-l532a-189916/) which confirms my theories. Sorry, try taking it back to where you bought it to get it fixed.

---

