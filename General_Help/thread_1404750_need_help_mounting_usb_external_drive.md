---
title: "need help mounting usb external drive"
date: 2010-02-11
forum: General Help
---

### Post by garyed on 2010-02-11
I just got a usb drive adapter that I plug my old internal 2 1/2" HD into 
& than plug it in to the usb port on my computer. I can mount the fat32 partition on the drive O.K. but I can't mount the ntfs partition. Its the /dev/sdd Disk.
Any help appreciated.
Here are the results of my fdisk -l:
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92819281

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005598e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6079    48829536   83  Linux
/dev/sdb2            6080       19457   107458785    5  Extended
/dev/sdb5           18701       19457     6080571   82  Linux swap / Solaris
/dev/sdb6            6080       12158    48829504+  83  Linux
/dev/sdb7           18182       18700     4168836   82  Linux swap / Solaris
/dev/sdb8           12159       18181    48379716   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92c092c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdd: 36.5 GB, 36487816192 bytes
240 heads, 63 sectors/track, 4713 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x3210320f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2356    17811328+   7  HPFS/NTFS
/dev/sdd2            2357        4713    17818920    f  W95 Ext'd (LBA)
/dev/sdd5            2357        4713    17818888+   b  W95 FAT32


---

### Post by whitehaint on 2010-02-11
Does it not show the drive or just refuse to mount? This link may have some helpful info to manually mount the volume, [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by Zimmer on 2010-02-11
Quick answer would be to right click on the Gnome Panel and Add to Panel and add Disk Mounter, a jolly useful little app that displays the any attached drives as icons on the Gnome panel and by left clicking on the icons you can mount and unmount them... ( I have not issued or written a mount command since I discovered this...)

If the Disk Mounter does not see the drive then it may be time to consult the logs to get a clue or two...

Hope this helps...

---

### Post by samantha_ on 2010-02-11
> **garyed said:**
> I just got a usb drive adapter that I plug my old internal 2 1/2" HD into 
& than plug it in to the usb port on my computer. I can mount the fat32 partition on the drive O.K. but I can't mount the ntfs partition. Its the /dev/sdd Disk.
Any help appreciated.
Here are the results of my fdisk -l:

tried ntfs-config yet?

---

### Post by abhishek.malhotra35 on 2010-02-11
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html).

---

### Post by garyed on 2010-02-11
Thanks for all the replies,
I've tried all the suggestions & readings but so far nothing has worked.
The fat32 partition mounts fine but the ntfs just won't.
Here's the error I get

```
sudo mount -t ntfs-3g /dev/sdd1 /media/usb_d1
```
> 
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read first NTFS_BLOCK_SIZE bytes of potential restart page.
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

The only way I've been able to read the ntfs partition is pull my internal HD out of my laptop &  put this problem drive into my laptop & boot from a live CD & force mount it. It could be a problem with the hardware I bought that adapts the drive to usb but if so why is it only the ntfs partition thats having the problem? Very wierd.

---

