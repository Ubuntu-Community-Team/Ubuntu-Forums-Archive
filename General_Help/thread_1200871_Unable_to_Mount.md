---
title: "Unable to Mount"
date: 2009-06-30
forum: General Help
---

### Post by dsmithnc on 2009-06-30
I'm trying to extract data from a 2.5" sata hd.  The laptop failed and I'd like to get the data from it.

When I try to mount it in Ubuntu if fails with the following details:

[IMG]http://ncsmiths.com/ubuntu/unable.png[/IMG]

I can, however, extract data if I boot into windows.

Dick

---

### Post by BrandonBan6 on 2009-06-30
What happens when you try the suggested command?

```

sudo mount -t ntfs-3g -o remove_hiberfile /dev/sde1 /media/disk-2

```

---

### Post by dsmithnc on 2009-06-30
> **BrandonBan6 said:**
> What happens when you try the suggested command?

```

sudo mount -t ntfs-3g -o remove_hiberfile /dev/sde1 /media/disk-2

```

I get this:

ntfs-3g: Failed to access volume '/dev/sde1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

---

### Post by BrandonBan6 on 2009-06-30
Okay, can you post the output of 'sudo fdisk -l' ? 

> **dsmithnc said:**
> I get this:

ntfs-3g: Failed to access volume '/dev/sde1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

---

### Post by dsmithnc on 2009-06-30
> **BrandonBan6 said:**
> Okay, can you post the output of 'sudo fdisk -l' ?

Here 'tis:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40cea6d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30027   241191846   83  Linux
/dev/sda2           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x024446e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12240    98317768+   7  HPFS/NTFS
/dev/sdb2           12241       38913   214250872+   f  W95 Ext'd (LBA)
/dev/sdb5           12241       38913   214250841    7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x640e2e7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14593   117218241    c  W95 FAT32 (LBA)
/dev/sdc2           14594       14946     2835472+   5  Extended
/dev/sdc5           14594       14780     1502046   83  Linux
/dev/sdc6           14781       14818      305203+  82  Linux swap / Solaris
/dev/sdc7           14819       14946     1028128+  83  Linux

Disk /dev/sdd: 8032 MB, 8032092160 bytes
131 heads, 50 sectors/track, 2395 cylinders
Units = cylinders of 6550 * 512 = 3353600 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2        2396     7839744    b  W95 FAT32

Ooopd lookd like
 it's not there now!

---

### Post by BrandonBan6 on 2009-06-30
Thanks, 

Is this a 320 GB drive? 

If yes, then try (note the change from the original command):
```

sudo mount -t ntfs-3g -o remove_hiberfile /dev/sdb1 /media/disk-2

```

You have a lot of HDD partitions LOL.

---

### Post by dsmithnc on 2009-06-30
Updated output of fdisk -l.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40cea6d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30027   241191846   83  Linux
/dev/sda2           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x024446e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12240    98317768+   7  HPFS/NTFS
/dev/sdb2           12241       38913   214250872+   f  W95 Ext'd (LBA)
/dev/sdb5           12241       38913   214250841    7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x640e2e7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14593   117218241    c  W95 FAT32 (LBA)
/dev/sdc2           14594       14946     2835472+   5  Extended
/dev/sdc5           14594       14780     1502046   83  Linux
/dev/sdc6           14781       14818      305203+  82  Linux swap / Solaris
/dev/sdc7           14819       14946     1028128+  83  Linux

Disk /dev/sdd: 8032 MB, 8032092160 bytes
131 heads, 50 sectors/track, 2395 cylinders
Units = cylinders of 6550 * 512 = 3353600 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2        2396     7839744    b  W95 FAT32

Disk /dev/sde: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72fb72fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       11764    94494298+   7  HPFS/NTFS
/dev/sde2           11766       12161     3180870   49  Unknown
Partition 2 does not end on cylinder boundary.

---

### Post by dsmithnc on 2009-06-30
> **BrandonBan6 said:**
> Thanks, 

Is this a 320 GB drive? 

If yes, then try (note the change from the original command):
```

sudo mount -t ntfs-3g -o remove_hiberfile /dev/sdb1 /media/disk-2

```

You have a lot of HDD partitions LOL.

Don't I though.  Fault of combining old os's and such.  One of these days I'll clean it up!

It's not the 320.  I just posted an updated output, the drive is showing now, it's a 100gb drive.

Dick

---

### Post by dsmithnc on 2009-06-30
When I tried again, I got this:

sudo mount -t ntfs-3g -o remove_hiberfile /dev/sde1 /media/disk-2fuse: failed to access mountpoint /media/disk-2: No such file or directory

---

### Post by BrandonBan6 on 2009-06-30
Well, we are getting closer :) 

```

sudo mkdir /media/disk-2
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sde1 /media/disk-2

```

If that still fails, I believe there is a force tag option for NTFS, i'm looking that up.

---

### Post by dsmithnc on 2009-06-30
> **BrandonBan6 said:**
> Well, we are getting closer :) 

```

sudo mkdir /media/disk-2
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sde1 /media/disk-2

```

If that still fails, I believe there is a force tag option for NTFS, i'm looking that up.

How can I thank you?  That worked perfectly.  Now I can access those files.

Thanks again Brandon.

Dick

---

### Post by BrandonBan6 on 2009-06-30
> **dsmithnc said:**
> How can I thank you?  That worked perfectly.  Now I can access those files.

Thanks again Brandon.

Dick

Hehe, sweeeet. No problem...Next comes the fun job of cleaning up those partitions :P

---

