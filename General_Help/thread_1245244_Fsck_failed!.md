---
title: "Fsck failed!"
date: 2009-08-20
forum: General Help
---

### Post by 4t0m1c_w07f on 2009-08-20
Hi.
I have 32bit and 64bit installations of ubuntu and are both giving the same error.. On boot it attempts do a file system check and then abruptly stops and says it has failed and drops to the root console.. This is the output from the log that was saved:

```
Log of fsck -C -R -A -a
Thu Aug 20 15:31:59 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sdc1: clean, 598237/27926528 files, 103896701/111699937 blocks
fsck.ext3: Unable to resolve 'UUID=069bd1a0-b218-4989-8b25-d8ecb08f4d85'
fsck died with exit status 8

Thu Aug 20 15:32:00 2009
----------------
```

Due to this I am not able to even log in because it says that the $HOME folder is missing... This is occuring in both the 32bit and 64bit installations...

---

### Post by mcduck on 2009-08-20
You have some partition badly defined in your /etc/fstab file.

To be precise, the partition's UUID is incorrect, so fsck tries to check a partition that doesn't exist. Check the correct UUID's for your partititons by running "blkid", and then edit fstab accordingly.

Also make sure that only root partition has fsck order "1" (the last number in the fstab entry lines). For other partitions you should use "2" to check them after root, or "0" to not check them at all.

---

### Post by 4t0m1c_w07f on 2009-08-20
Thanks for the reply.. I changed everything accordingly but when I try to copy over the old fstab it gave me a read-only error..

---

### Post by s3a on 2009-08-20
To write, you need to be root.

---

### Post by 4t0m1c_w07f on 2009-08-20
I was root... But I found the bigger problem.. When it first gave the error, it was trying to check a uuid that doesn't exist (ie UUID=069bd1a0-b218-4989-8b25-d8ecb08f4d85) which it claims is sdc3.. Here is a copy of my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[B]# / was on /dev/sdc3 during installation
UUID=9034fe60-d788-4543-81b2-06b66e5010aa /               ext4    relatime,errors=remount-ro 0       1[/B]
# /home was on /dev/sdc1 during installation
UUID=b7be4252-3223-497b-b3aa-bee5660234b9 /home           ext3    relatime        0       2
# /media/80kG_C4 was on /dev/sdb2 during installation
# UUID=6fe7c612-a776-40f4-bad5-b88697474ecf /media/80kG_C4  ext3    relatime        0       2
# /media/DozI3 was on /dev/sdb1 during installation
UUID=6AE09450E094247B /media/DozI3    ntfs    defaults,nls=utf8,umask=007,gid=46 0       2
# /media/V1st@ was on /dev/sdb2 during installation
UUID=1672428B72427013 /media/V1st@    ntfs    defaults,nls=utf8,umask=007,gid=46 0       2
# /media/w0rmp1e was on /dev/sda1 during installation
UUID=069bd1a0-b218-4989-8b25-d8ecb08f4d85 /media/w0rmp1e  ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=85e7082c-5154-4f72-8476-330e30d4ccb2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Tell me what to do.. Thanks

---

### Post by mcduck on 2009-08-20
> **4t0m1c_w07f said:**
> Thanks for the reply.. I changed everything accordingly but when I try to copy over the old fstab it gave me a read-only error..

If you can still get into the recovery mode you should be able to edit the file directly withou any roblems, as recovery consoloe logs you in as root.

If you use a live-CD or some other way than the recovery mode then you need to open the editor using "sudo" (for console editors) or "gksudo" (for graphical editors).

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by mcduck on 2009-08-20
> **4t0m1c_w07f said:**
> I was root... But I found the bigger problem.. When it first gave the error, it was trying to check a uuid that doesn't exist (ie UUID=069bd1a0-b218-4989-8b25-d8ecb08f4d85) which it claims is sdc3.. Here is a copy of my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[B]# / was on /dev/sdc3 during installation
UUID=9034fe60-d788-4543-81b2-06b66e5010aa /               ext4    relatime,errors=remount-ro 0       1[/B]
# /home was on /dev/sdc1 during installation
UUID=b7be4252-3223-497b-b3aa-bee5660234b9 /home           ext3    relatime        0       2
# /media/80kG_C4 was on /dev/sdb2 during installation
# UUID=6fe7c612-a776-40f4-bad5-b88697474ecf /media/80kG_C4  ext3    relatime        0       2
# /media/DozI3 was on /dev/sdb1 during installation
UUID=6AE09450E094247B /media/DozI3    ntfs    defaults,nls=utf8,umask=007,gid=46 0       2
# /media/V1st@ was on /dev/sdb2 during installation
UUID=1672428B72427013 /media/V1st@    ntfs    defaults,nls=utf8,umask=007,gid=46 0       2
# /media/w0rmp1e was on /dev/sda1 during installation
UUID=069bd1a0-b218-4989-8b25-d8ecb08f4d85 /media/w0rmp1e  ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=85e7082c-5154-4f72-8476-330e30d4ccb2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Tell me what to do.. Thanks
Could you post the outputs of "sudo fdisk -l" and "blkid" here as well. It's pretty much impossible to tell you the exact changes you need to do to fstab without knowing your partititon layout and the correct UUIDs.. ;)

---

### Post by 4t0m1c_w07f on 2009-08-20
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046d95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x100f59dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8493    68219991    7  HPFS/NTFS
/dev/sdb2            8494       19458    88068096    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003712b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       55624   446799748+  83  Linux
/dev/sdc2           55625       56353     5855692+  82  Linux swap / Solaris
/dev/sdc3   *       56354       58265    15358140   83  Linux
/dev/sdc4           58266       60801    20370420   83  Linux

Disk /dev/sdd: 131 MB, 131072000 bytes
9 heads, 32 sectors/track, 888 cylinders
Units = cylinders of 288 * 512 = 147456 bytes
Disk identifier: 0x3fff0502

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         889      127983    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1000, 8, 32) logical=(888, 7, 30)

```

```
root@4t0m1c-w0rM:/home# blkid
/dev/sdc1: UUID="b7be4252-3223-497b-b3aa-bee5660234b9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="6AE09450E094247B" TYPE="ntfs" 
/dev/sdb2: UUID="1672428B72427013" TYPE="ntfs" 
/dev/sdc2: TYPE="swap" UUID="85e7082c-5154-4f72-8476-330e30d4ccb2" 
/dev/sdc3: UUID="6977984f-b58e-4310-a2ad-2ff2cba436d1" TYPE="ext4" 
/dev/sdc4: UUID="9034fe60-d788-4543-81b2-06b66e5010aa" TYPE="ext4" 
/dev/sda1: LABEL="w0rMp13" UUID="14cf256e-a0a3-4e79-bd52-5693d37d3cb7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: LABEL="ATOMIC WOLF" UUID="D0D2-44FA" TYPE="vfat" 
```

I figured out the culprit.. It was my old 500gb that died and got replaced..

---

### Post by 4t0m1c_w07f on 2009-08-20
I think this is what my fstab should look like:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc4 during installation
UUID=9034fe60-d788-4543-81b2-06b66e5010aa /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdc1 during installation
UUID=b7be4252-3223-497b-b3aa-bee5660234b9 /home           ext3    relatime        0       2
# /media/DozI3 was on /dev/sdb1 during installation
UUID=6AE09450E094247B /media/DozI3    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /media/V1st@ was on /dev/sdb2 during installation
UUID=1672428B72427013 /media/V1st@    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /media/w0rmp1e was on /dev/sda1 during installation
UUID=14cf256e-a0a3-4e79-bd52-5693d37d3cb7 /media/w0rmp1e  ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=85e7082c-5154-4f72-8476-330e30d4ccb2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by mcduck on 2009-08-20
> **4t0m1c_w07f said:**
> I think this is what my fstab should look like:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc4 during installation
UUID=9034fe60-d788-4543-81b2-06b66e5010aa /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdc1 during installation
UUID=b7be4252-3223-497b-b3aa-bee5660234b9 /home           ext3    relatime        0       2
# /media/DozI3 was on /dev/sdb1 during installation
UUID=6AE09450E094247B /media/DozI3    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /media/V1st@ was on /dev/sdb2 during installation
UUID=1672428B72427013 /media/V1st@    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /media/w0rmp1e was on /dev/sda1 during installation
UUID=14cf256e-a0a3-4e79-bd52-5693d37d3cb7 /media/w0rmp1e  ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=85e7082c-5154-4f72-8476-330e30d4ccb2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Yes, that seems about correct. You should probably change the last number on the NTFS entries to "2" or "0", though. "1" shouldn't be used for others than the root partition.

---

### Post by 4t0m1c_w07f on 2009-08-20
Thanks that worked for my 64bit installation but my 32 is still giving problems... :( [IMG]http://img200.imageshack.us/img200/4594/dsc00511sxm.jpg[/IMG] Just some extra info... my 32 and 64 are sharing the same $HOME folder..

---

### Post by mcduck on 2009-08-20
Did you edit the /etc/fstab in both Linux installs? Even though they share some partitions, they both have their own configuration files...

Anyway, that wouls mean that it has detected some problems in your root partition, probably nothing serious but you should do what it suggests and run "fsck /dev/sdc4" to execute a manual chekc on that partition.

You will probably get some messages about broken inodes (or something like that) and if you want  to fix them. Just answer "yes" to them and fsck will try to fix the filesystem.

Any broken files will be moved to /lost+found, you can check afterwards if there's anything important. Usually it's just some temp files and other meaningless stuff.

---

### Post by 4t0m1c_w07f on 2009-08-20
Thanks a lot! Everything now working perfectly!! :guitar:

---

