---
title: "MDADM Superblock Recovery"
date: 2011-10-19
forum: General Help
---

### Post by Teque5 on 2011-10-19
After a power cycle I found my RAID 5 Array no longer working. I tried various methods to reassemble the array but nothing has worked so far. _I believe I need to recreate the superblocks and UUIDs somehow_, but was reluctant to barrel into something as to not lose a bunch of data. Thanks for reading.

```
cat /etc/mdadm/mdadm.conf

    DEVICE partitions
    ARRAY /dev/md0 level=raid5 num-devices=4 metadata=0.90 UUID=fd522a0f:2de72d76:f2afdfe9:5e3c9df1
    MAILADDR root
```

Which is normal. It should have 4x2000GB drives (sda, sdc, sde, sdd).

```
cat /proc/mdstat

    Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
    md0 : inactive sdd[1](S)
      1953514496 blocks
       
    unused devices: <none>
```

This is a problem. It only shows one drive in the array and it is also inactive. The array should have sda, sdc, and sde in there as well. When I do a `mdadm --examine /dev/sdd` everything looks fine. On the other drives examine says **no RAID superblock on /dev/sdX**.

```
mdadm --examine --scan

    ARRAY /dev/md0 level=raid5 num-devices=4 metadata=0.90 UUID=fd522a0f:2de72d76:f2afdfe9:5e3c9df1
```

No help there.

```
mdadm --assemble --scan -v

    mdadm: looking for devices for /dev/md0
    mdadm: no RAID superblock on /dev/sde
    mdadm: /dev/sde has wrong uuid.
    mdadm: cannot open device /dev/sdd: Device or resource busy
    mdadm: /dev/sdd has wrong uuid.
    mdadm: no RAID superblock on /dev/sdc
    mdadm: /dev/sdc has wrong uuid.
    mdadm: cannot open device /dev/sdb5: Device or resource busy
    mdadm: /dev/sdb5 has wrong uuid.
    mdadm: no RAID superblock on /dev/sdb2
    mdadm: /dev/sdb2 has wrong uuid.
    mdadm: cannot open device /dev/sdb1: Device or resource busy
    mdadm: /dev/sdb1 has wrong uuid.
    mdadm: cannot open device /dev/sdb: Device or resource busy
    mdadm: /dev/sdb has wrong uuid.
    mdadm: no RAID superblock on /dev/sda
    mdadm: /dev/sda has wrong uuid.
```

From this it looks like I have no UUIDs and no Superblocks for sda, sdc, and sde.

```
sudo fdisk -l

    Disk /dev/sda: 2000.4 GB, 2000397852160 bytes
    255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/sda doesn't contain a valid partition table
                
    Disk /dev/sdb: 250.1 GB, 250058268160 bytes
    255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x353cf669
    
    Device Boot      Start         End      Blocks   Id  System
    /dev/sdb1              63   476327249   238163593+  83  Linux
    /dev/sdb2       476327250   488392064     6032407+   5  Extended
    /dev/sdb5       476327313   488392064     6032376   82  Linux swap / Solaris
    
    Disk /dev/sdc: 2000.4 GB, 2000397852160 bytes
    255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/sdc doesn't contain a valid partition table
    
    Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
    255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/sdd doesn't contain a valid partition table
    
    Disk /dev/sde: 2000.4 GB, 2000397852160 bytes
    255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/sde doesn't contain a valid partition table
```

So from this it looks like none of my RAID disks have a partition table or UUID. The closest thing I found to my problem was [this thread]("http://arstechnica.com/civis/viewtopic.php?f=16&t=121767"), which suggested running `mdadm --create /dev/md0 -v -l 5 -n 4 /dev/sda /dev/sdc /dev/sde /dev/sdd` and checking for a valid filesystem with `fsck -fn /dev/md0`. However, the first command spit out `mdadm: no raid-devices specified.` I retried the command using sda1, sdc1, etc, but then I get this:

    ```
mdadm: layout defaults to left-symmetric
    mdadm: chunk size defaults to 512K
    mdadm: layout defaults to left-symmetric
    mdadm: layout defaults to left-symmetric
    mdadm: super1.x cannot open /dev/sda1: No such file or directory
    mdadm: ddf: Cannot open /dev/sda1: No such file or directory
    mdadm: Cannot open /dev/sda1: No such file or directory
    mdadm: device /dev/sda1 not suitable for any style of array
```

If I do a create and leave sda1 as a "missing" variable in the command then it just says the same thing for sdc1.

**I am sure that I am making this more complicated than it needs to be. Can someone with experience please help me? Thanks for your time in advance.**

---

### Post by Teque5 on 2011-10-19
In [this thread]("http://askubuntu.com/questions/69086/mdadm-superblock-recovery-10-paypal-bounty") someone suggested using the dumpe2fs tools to recover the superblock. You can still see a filesystem on the drives:

```
dumpe2fs /dev/sda
dumpe2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          bbe6fb91-d37c-414a-8c2b-c76a30b9b5c5
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              366288896
Block count:              1465135872
Reserved block count:     73256793
Free blocks:              568552005
Free inodes:              366066972
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      674
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Filesystem created:       Wed Oct 28 12:23:09 2009
Last mount time:          Tue Oct 18 13:59:36 2011
Last write time:          Tue Oct 18 13:59:36 2011
Mount count:              17
Maximum mount count:      26
Last checked:             Fri Oct 14 17:04:16 2011
Check interval:           15552000 (6 months)
Next check after:         Wed Apr 11 17:04:16 2012
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      17e784d8-012e-4a29-9bbd-c312de282588
Journal backup:           inode blocks
Journal superblock magic number invalid!
```

But I don't know how to restore the superblocks and UUIDs. One place had a method using fsck but I dont want to corrupt the raid filesystem.

---

### Post by Teque5 on 2011-10-20
[This thread was finished over at Overclockers.com]("http://www.overclockers.com/forums/showthread.php?t=689300").

---

