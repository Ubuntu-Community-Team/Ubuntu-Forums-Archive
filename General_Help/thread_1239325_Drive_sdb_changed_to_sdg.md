---
title: "Drive sdb changed to sdg?"
date: 2009-08-13
forum: General Help
---

### Post by blur xc on 2009-08-13
Well, I couldn't mount my 1tb drive-

```
/dev$ sudo mount -t ntfs-3g /dev/sdb1 /media/FreeAgent_Drive
Error opening '/dev/sdb': No medium found
Failed to mount '/dev/sdb': No medium found

```

so then I just ran:
```
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008be87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12748   102398278+  83  Linux
/dev/sda2   *       12749       24398    93577216    7  HPFS/NTFS
/dev/sda3           24399       58303   272341912+  83  Linux
/dev/sda4           59579       60801     9823747+   5  Extended
/dev/sda5           59579       60801     9823716   82  Linux swap / Solaris

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f9b38fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121601   976760001    7  HPFS/NTFS
```

and noticed that sdb turned into sdg.  Why would my device change "drive letters" for a lack of a better term?  Now I need to edit my fstab?  How do I keep this from happening?

Thanks,
BM

---

### Post by michy99 on 2009-08-13
The /dev/sdXX designation can change depending on the order in which the system finds your drives on boot-up. That is why it is better to use the UUID in fstab. To find the UUIDs of your partitions, run```
sudo blkid
``` To use them in the fstab file. replace the /dev/sda4 type designation with UUID=9664C43A28AA28AA type instead. Notice that fstab does not use the quote marks that blkid does.

---

### Post by blur xc on 2009-08-13
Awesome- I did notice that the boot and swap partitions are identified by the uuid number.  I wondered if that was the better way to go, but didn't know where to find the information.

Thanks!
BM

---

### Post by doas777 on 2009-08-13
UUID takes care of almost everything except grub hd(x,y). it's a good trick.
when you mount by UUID it doesn't matter what sdXY name you have now or had last time, since the disk can always be identified.

---

