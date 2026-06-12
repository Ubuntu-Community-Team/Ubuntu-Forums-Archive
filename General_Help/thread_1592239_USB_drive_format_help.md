---
title: "USB drive format help"
date: 2010-10-10
forum: General Help
---

### Post by Vishnu V on 2010-10-10
Hi
 I had  4 GB usb drive ( USBest USB2FlashStorage ). It is not working now.
The command 
```
sudo fdisk -l
```doesnot shows the drive. But Disk utility shows the drive and gives device as /dev/sdb


When i tried to format using mkfs and fdisk it shows following errors
```
root@vishnu-laptop:/home/vishnu# mkfs.ext3 /dev/sdb
mke2fs 1.41.11 (14-Mar-2010)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
mkfs.ext3: No medium found while trying to determine filesystem size
root@vishnu-laptop:/home/vishnu# fdisk /dev/sdb

Unable to open /dev/sdb

```

Please help me to format

---

### Post by coffeecat on 2010-10-10
If you want to format the drive from the terminal, you need to make a blank partition with fdisk first and then use mke2fs to create the filesystem in the partition. There are no partitions on your USB drive.

Why not use Disk Utility instead? It's far easier. And the advantage of using Disk Utility for this is that if you create an ext2/3 partition with it you are given the option of "owning" the filesystem. Which means that you won't be troubled by permissions issues if you are the only user of the USB drive.

---

### Post by Vishnu V on 2010-11-17
When i tried to format it using disk utility i got the following error
```

Error creating partition table: helper exited with exit code 1: cannot open /dev/sdb: No medium found

```



Sorry for the late response

Thanks

---

