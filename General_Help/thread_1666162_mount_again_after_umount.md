---
title: "mount again after umount???"
date: 2011-01-13
forum: General Help
---

### Post by ethan86 on 2011-01-13
i am new to linux because i'm studying linux as a module required by diploma course. I'm just testing mount again after umount the drive but it said "can't find /dev/sdg1 in /etc/fstab or /etc/mtab"  so i just want to know am i still able to mount the drive again after i umount it?

---

### Post by 3Miro on 2011-01-13
> **ethan86 said:**
> i am new to linux because i'm studying linux as a module required by diploma course. I'm just testing mount again after umount the drive but it said "can't find /dev/sdg1 in /etc/fstab or /etc/mtab"  so i just want to know am i still able to mount the drive again after i umount it?

/dev/sdg1, are you sure it is not sdb1

You should be able to mount an unmounted drive in the same way you mounted it in the first place.

---

### Post by ethan86 on 2011-01-13
The result of sudo fdisk -l is below

"Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x89059c73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       24027   192892928    7  HPFS/NTFS
/dev/sda3           24028       30402    51201025    5  Extended
/dev/sda5           24028       24635     4881408   82  Linux swap / Solaris
/dev/sda6           24635       30402    46318592   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014836

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdg: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00016fe2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1      182401  1465136001    7  HPFS/NTFS"


root@ethan-desktop:/boot# mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
root@ethan-desktop:/boot# sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab


i tried to mount sdb1 and i got this error :)

---

### Post by coypu76 on 2011-01-13
> **3Miro said:**
> /dev/sdg1, are you sure it is not sdb1

You should be able to mount an unmounted drive in the same way you mounted it in the first place.

I concur - execute
sudo fdisk -l

to list the currently available disk devices.  Make sure you are using the proper device name in the mount command.
Hope this helps - good luck!

---

### Post by 3Miro on 2011-01-13
> **ethan86 said:**
> 
root@ethan-desktop:/boot# mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
root@ethan-desktop:/boot# sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab


Mount associates a device with a folder. mount /dev/sdg1 says "associate sdg1 with ...." you need to give it a folder:

```
mkdir /media/some_folder_name
mount /dev/sdg1 /media/some_folder_name
```

The /etc/fstab and /etc/mtab can be used to permanently associate devices with folders, so you can then just say "mount folder" or "mount device" at it will know what to do.

---

### Post by ethan86 on 2011-01-13
thanks a lot that solved my problem :)

---

