---
title: "corrupt Partition or not - gparted and filesystem report different used spaces"
date: 2009-07-30
forum: General Help
---

### Post by ben trovato on 2009-07-30
Interesting confusion (I think).

A windows 7RC install failed on a partition of this disk.  It was deleted and the ubuntu liveCD was used to install jaunty. with /swap, /, and /home partitions.

Everything is working fine.

gparted shows the /home partition as about 75% full (79 / 108 Gb),
but there's only about 20 Gb in it according to the filesystem.

So, who is right? Am I misinterpreting the information? 

I initially considered this a partition table problem and started gpart to investigate; but I'm not sure what category to put it in.

Below are the results of 
gpart /dev/sbd
cat /etc/fstab
fdisk -lu
cat /proc/cmdline

```


robert@thomas-ubuntu:~$ sudo gpart /dev/sdb
[sudo] password for robert: 

Begin scan...
Possible partition(Linux swap), size(3812mb), offset(0mb)
Possible extended partition at offset(3812mb)
   Possible partition(Linux ext2), size(37220mb), offset(3812mb)
   Possible partition(Linux ext2), size(51591mb), offset(41033mb)
Possible extended partition at offset(92624mb)
   Possible partition(Windows NT/W2K FS), size(60000mb), offset(92624mb)
End scan.

Checking partitions...
Partition(Linux swap or Solaris/x86): primary 
   Partition(Linux ext2 filesystem): logical 
   Partition(Linux ext2 filesystem): logical 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Number of inconsistencies found: 1.

Guessed primary partition table:
Primary partition(1)
   type: 130(0x82)(Linux swap or Solaris/x86)
   size: 3812mb #s(7807520) s(63-7807582)
   chs:  (0/1/1)-(485/254/56)d (0/1/1)-(485/254/56)r

Primary partition(2)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 148813mb #s(304769115) s(7807590-312576704)
   chs:  (486/0/1)-(1023/254/63)d (486/0/1)-(19456/254/63)r

Primary partition(3)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 60000mb #s(122881122) s(189695583-312576704)
   chs:  (1023/254/63)-(1023/254/63)d (11808/1/1)-(19456/254/63)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

robert@thomas-ubuntu:~$ 
==============================================================================

robert@thomas-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=88cd71b4-cf38-4cf9-a62a-ca7f59db361d /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=cbe52601-69e4-4622-9a69-92dd244b45f7 /home           ext3    relatime        0       2
# swap was on /dev/sdb1 during installation
UUID=247e10e9-ca38-4bab-9cc1-4ced6b8b0fba none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
robert@thomas-ubuntu:~$ 

===============================================================================

robert@thomas-ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd820d820

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   240091424   120045681    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0fff0ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     7807589     3903763+  82  Linux swap / Solaris
/dev/sdb2         7807590   312576704   152384557+   5  Extended
/dev/sdb5         7807653    84036014    38114181   83  Linux
/dev/sdb6        84036078   312576704   114270313+  83  Linux
robert@thomas-ubuntu:~$ 


===============================================================================

robert@thomas-ubuntu:~$ cat /proc/cmdline
root=UUID=88cd71b4-cf38-4cf9-a62a-ca7f59db361d ro quiet splash vga=795
robert@thomas-ubuntu:~$ 

===============================================================================

```

---

### Post by rwgale on 2009-08-04
A similar problem has been reported, compare:

[http://ubuntuforums.org/showthread.php?t=891730]("http://ubuntuforums.org/showthread.php?t=891730")

The pertinent passage seems to be:

[INDENT]...is that gparted is showing the "used" space in the partition as 51GB which is plainly wrong. The partition size appears correct though.

tune2fs seems to have confirmed that the file-system inside partition sda5 is 28GB, and fdisk seems to confirm the partition size is ~55GB.

If it weren't for the incorrect report by gparted I'd say all it needs is the file-system extending. To do that you'd boot the PC using a LiveCD so the PC's root file-system can be manipulated.

sudo umount /dev/sda5
sudo tune2fs -O ^has_journal /dev/sda5
sudo resize2fs /dev/sda5
sudo fsck -n /dev/sda5
sudo tune2fs -j /dev/sda5

At that point the file-system should have expanded to fill the partition it is in, and the PC can be booted from the hard disk again as normal.[/INDENT]

Compare these symptoms with yours and consider file-system extending with the liveCD  [backup SDB6 (/home) first].

Best Regards,
Robert

---

### Post by ben trovato on 2009-08-05
I checked the dump of /dev/sdb6 as per the link you provided:

```
ubuntu@ubuntu:~$ sudo dumpe2fs -h /dev/sdb6
dumpe2fs 1.41.4 (27-Jan-2009)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          cbe52601-69e4-4622-9a69-92dd244b45f7
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed_directory_hash
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              3303104
Block count:              13207430
Reserved block count:     660371
Free blocks:              8243458
Free inodes:              3299026
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1020
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8176
Inode blocks per group:   511
Filesystem created:       Sun Jun 21 14:29:50 2009
Last mount time:          Wed Aug  5 16:04:36 2009
Last write time:          Wed Aug  5 16:06:15 2009
Mount count:              15
Maximum mount count:      21
Last checked:             Wed Jul 29 20:39:55 2009
Check interval:           15552000 (6 months)
Next check after:         Mon Jan 25 20:39:55 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      0ac9eb43-e3a3-46a6-969a-b4f8d84b38bc
Journal backup:           inode blocks
Journal size:             128M

ubuntu@ubuntu:~$ 
```

and then ran the following (also from the link):
```

ubuntu@ubuntu:~$ sudo umount /dev/sdb6
ubuntu@ubuntu:~$ sudo tune2fs -O ^has_journal /dev/sdb6
tune2fs 1.41.4 (27-Jan-2009)
ubuntu@ubuntu:~$ sudo resize2fs /dev/sdb6
resize2fs 1.41.4 (27-Jan-2009)
Please run 'e2fsck -f /dev/sdb6' first.

ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sdb6
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb6: 4078/3303104 files (8.6% non-contiguous), 4931171/13207430 blocks
ubuntu@ubuntu:~$ sudo resize2fs /dev/sdb6
resize2fs 1.41.4 (27-Jan-2009)
Resizing the filesystem on /dev/sdb6 to 28567578 (4k) blocks.
The filesystem on /dev/sdb6 is now 28567578 blocks long.

ubuntu@ubuntu:~$ sudo tune2fs -j /dev/sdb6
tune2fs 1.41.4 (27-Jan-2009)
Creating journal inode: done
This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
ubuntu@ubuntu:~$
```

The main difference is the request to  -- Please run 'e2fsck -f /dev/sdb6' first.

else, all was fine.

Rebooted the system and viola!
gparted, disk analyzer, system monitor, and the file-system all agree.


Many Thanks.

---

