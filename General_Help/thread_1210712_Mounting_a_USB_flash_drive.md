---
title: "Mounting a USB flash drive"
date: 2009-07-11
forum: General Help
---

### Post by Gamfrek on 2009-07-11
I was taught a while ago how to do this, but I forgot. The thing I'm having the most trouble with is where the location of the flash drive is, so I can go into the terminal and say...

mount <location>

What I'm trying to do is download a file and then take it to my Windows computer...

---

### Post by Gamfrek on 2009-07-11
bump

---

### Post by yeaitsdark on 2009-07-11
First just find out which device is your flash drive. 

```
sudo fdisk -l
```

Then based on the output, which will look like this.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001ee9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38161   306528201   83  Linux
/dev/sda2           38162       38913     6040440    5  Extended
/dev/sda5           38162       38913     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b50a0a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         xx       xx       xx  Fat32

It will be the 16.0 GB (or whatever size). Then simply make the folder where you wish to mount it. For example:
```
sudo mkdir /media/usb
```
Then mount said device.
```
sudo mount /dev/**sdb1** /media/usb
```

Where sdb1 is the drive you have ascertained above.

---

### Post by Gamfrek on 2009-07-11
I didn't get anything like 16.0 GB or whatever...

---

### Post by yeaitsdark on 2009-07-11
Well post the output for that for me then and I'll check it out. also unplug and replug the device if you are still not seeing anything besides your primary hard disk.

---

### Post by Gamfrek on 2009-07-11
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03ef03ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12637   101506671    7  HPFS/NTFS
/dev/sda2           12964       29984   136721182+   5  Extended
/dev/sda5           12964       25121    97659103+  83  Linux
/dev/sda6           25122       29984    39062016   82  Linux swap / Solaris

---

### Post by Gamfrek on 2009-07-11
After plugging it back in.....

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03ef03ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12637   101506671    7  HPFS/NTFS
/dev/sda2           12964       29984   136721182+   5  Extended
/dev/sda5           12964       25121    97659103+  83  Linux
/dev/sda6           25122       29984    39062016   82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1967    15794144+   c  W95 FAT32 (LBA)

Jackpot! :p

---

### Post by yeaitsdark on 2009-07-11
Based on that your system is not seeing your flash drive at the moment. That output is only your hard drive. First, have you used the flash drive with Ubuntu before and it worked? Second, try a different USB port with the flash drive. 

Sometimes computers just do weird things to make our lives more frustrated. After you try another USB port, look at the output of fdisk -l again and see if you see another device - namely /dev/sdb1. Let me know.

---

### Post by yeaitsdark on 2009-07-11
OH lol nice! As I was writing my last reply you got it working :D Excellent.

---

### Post by Gamfrek on 2009-07-11
Thanks a MILLION!!!! :p

---

