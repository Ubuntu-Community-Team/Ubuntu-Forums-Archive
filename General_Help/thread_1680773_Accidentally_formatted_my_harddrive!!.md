---
title: "Accidentally formatted my harddrive!!"
date: 2011-02-03
forum: General Help
---

### Post by hodot on 2011-02-03
Hi,
I've been using Ubuntu 10.10 on my 750GB harddisk and suddenly yesterday, when I was trying to install VMWare ESXi on my 2nd harddisk (2TB), the ESXi was installed on the first harddisk that contained my Ubuntu!! All my backup data from my laptop and movies and what not worth nearly 600GB was lost!! Need your guys opinion on how to recover.

FYI, I have MacOSX 10.6.6 installed on the 2nd harddisk (2TB disk), and I've been trying to use TestDisk but not quite understand.

Some info on my previous Ubuntu setup (taken from my putty logs):

```
root@ixbuntu:~/downloads# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ixbuntu-root
                      677G  586G   57G  92% /
none                  1.8G  276K  1.8G   1% /dev
none                  1.9G  288K  1.9G   1% /dev/shm
none                  1.9G  720K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  677G  586G   57G  92% /var/lib/ureadahead/debugfs
/dev/sda1             228M   21M  196M  10% /boot
root@ixbuntu:~/downloads# 

```
Fdisk:

```
root@ixbuntu: ~root@ixbuntu:~# fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000191ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       91202   732322817    5  Extended
/dev/sda5              32       91202   732322816   8e  Linux LVM

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      243202  1953514583+  ee  GPT

Disk /dev/dm-0: 738.5 GB, 738495299584 bytes
255 heads, 63 sectors/track, 89783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 11.4 GB, 11400118272 bytes
255 heads, 63 sectors/track, 1385 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table
root@ixbuntu: ~root@ixbuntu:~#

```

Current partition table, after accidentally wiped out (ran from MacOSX) - currently PhotoRec running:

```
bash-3.2# diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *750.2 GB   disk0
   1:                 DOS_FAT_16                         4.3 GB     disk0s2
   2:                       0xFB                         744.9 GB   disk0s3
   3:               DOS_FAT_16_S Hypervisor0             4.2 MB     disk0s4
   4:                 DOS_FAT_16 Hypervisor1             262.1 MB   disk0s5
   5:                 DOS_FAT_16 Hypervisor2             262.1 MB   disk0s6
   6:                       0xFC                         115.3 MB   disk0s7
   7:                 DOS_FAT_16 Hypervisor3             299.9 MB   disk0s8
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *2.0 TB     disk1
   1:                        EFI                         209.7 MB   disk1s1
   2:                  Apple_HFS Snow                    200.0 GB   disk1s2
   3:                  Apple_HFS Part2                   1.8 TB     disk1s3
bash-3.2#
```

Please help.. at least give me some ideas..

Thanks in advance..

---

### Post by sikander3786 on 2011-02-03
I would recommend using photorec for at least recovering you files. It will not recover the file names but will at least recover the files. And don't use the drive before you restore your data or everything or part of it might get over-written.

See here if it is of any help.

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

And make sure you are saving your recovered data to some other HDD or you may over-write the existing one.

---

### Post by hodot on 2011-02-03
> **sikander3786 said:**
> I would recommend using photorec for at least recovering you files. It will not recover the file names but will at least recover the files. And don't use the drive before you restore your data or everything or part of it might get over-written.

See here if it is of any help.

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

And make sure you are saving your recovered data to some other HDD or you may over-write the existing one.

Thanks Sikander. I've tried Photorec but want to give TestDisk a shot.

Anyway, here what I can see with TestDisk:

```
Results
   * FAT16 <32M                    32       8191       8160 [Hypervisor0]
     FAT16, 4177 KB / 4080 KiB
     FAT16 LBA                   8224     520191     511968 [Hypervisor1]
     FAT16, 262 MB / 249 MiB
     Linux                     502142 1442875773 1442373632
     EXT4 Large file Sparse superblock Backup superblock, 738 GB / 687 GiB
     FAT16 LBA                 520224    1032191     511968 [Hypervisor2]
     FAT16, 262 MB / 249 MiB
     FAT16 LBA                1257504    1843199     585696 [Hypervisor3]
     FAT16, 299 MB / 285 MiB
   P Linux Swap            1442875776 1465141615   22265840
     SWAP2 version 1, 11 GB / 10 GiB

```

From my previous Fdisk (when Ubuntu still alive...):

```
root@ixbuntu:~# fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000191ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       91202   732322817    5  Extended
/dev/sda5              32       91202   732322816   8e  Linux LVM


```

/dev/sda1 = /boot starts from 1 until 32, and the rest "root partition" starts from 32 until the end

Taken from TestDisk result above, is it possible for me to somehow, "recreate" the deleted partition based on the fdisk result? Or is it I'm gonna make it worst?

---

### Post by srs5694 on 2011-02-03
You're probably out of luck; however, if you're very very very very very lucky, you could use fdisk to re-create your earlier partitions to get back your LVM and recover data. There are two reasons why this might not work, though:


[LIST]
[*]Your only partition table backup (your fdisk output) uses cylinder alignment values, which are insufficiently precise -- you don't know precisely what sector "cylinder 32" refers to. Without that knowledge, it'll be pure luck if you get the right sector value. Of course, you could try writing partition table after partition table with different values (try aligning to multiples ot 16065 sectors, 2048 sectors, and 63 sectors) in hopes of finding something, but it's still hit-or-miss. In the future, use fdisk's "-u" option to get sector-precise partition start and end points; or use "sfdisk -d /dev/sda > parts.txt" to get a backup file (parts.txt) that you can feed back into sfdisk to re-create your partition table.
[*]When VMWare started writing to your disk, it overwrote existing data. I don't know how much data it wrote or whether it overwrote any critical LVM or filesystem data. If it wrote just a few sectors, you might luck out and find that you can recover everything; however, even just one sector in the wrong place could make recovery of your complete filesystems very difficult. If VMWare wrote a lot of data, it could be that it simply overwrote everything of value and you'll never get it back. I don't know much about VMWare, so I don't know how much data it wrote or what else it might have done.
[/LIST]


TestDisk has options to perform scans with increasing "depth" (I think that's the word it uses, but I could be mistaken). You could try that, in hopes that it will find your LVM data or the filesystems that were in your LVM. (It would probably try to recover your logical volumes as partitions, but in your case I'd call that a great victory.) One possible problem with this approach is that logical volumes, unlike partitions, can be discontiguous. Thus, even if TestDisk detects a filesystem, it might not recover the whole filesystem, since that filesystem might have a gap in it, and TestDisk wouldn't be able to cope with that. In such a case, at best you'd get back a badly corrupted filesystem.

PhotoRec is more likely to work, but it will recover individual files, not entire filesystems. You'll probably have to identify each file individually, which will be a huge time drain.

Best of luck with your recovery efforts.

---

### Post by HermanAB on 2011-02-03
Photorec or ddrescue.

Then, eventually, enjoy your nice new freshly installed system...

---

### Post by hodot on 2011-02-03
Thanks srs5694 for such an info! Btw, if I want to write the new partition table, I think it is advisable for me to clone the disk and play with the partition table on that clone image instead of the physical disk, right? Can I just use dd to clone or it doesn't matter?

Btw, I did use "fdisk -l" to get the above output, can I just use them to recreate the partition table?

---

### Post by srs5694 on 2011-02-03
> **hodot said:**
> Thanks srs5694 for such an info! Btw, if I want to write the new partition table, I think it is advisable for me to clone the disk and play with the partition table on that clone image instead of the physical disk, right? Can I just use dd to clone or it doesn't matter?

Cloning the disk before doing anything dangerous is always advisable. In this case, rewriting something you hope to be the correct old partition table over a bad current one is only slightly dangerous, so long as you only attempt to read the partitions you create. The danger would be if you slip up and write the changed partitions.

> Btw, I did use "fdisk -l" to get the above output, can I just use them to recreate the partition table?

Oops; my bad. I meant "-u", as in "fdisk -lu". I've corrected the error in my earlier post in case somebody reads it in the future.

---

### Post by hodot on 2011-02-03
> Of course, you could try writing partition table after partition table with different values (try aligning to multiples ot 16065 sectors, 2048 sectors, and 63 sectors) in hopes of finding something, but it's still hit-or-miss.

Ok, I would like to beat the odds, but you got to help me to understand what you're saying there. Give some examples, perhaps?

Really appreciate your help

---

### Post by srs5694 on 2011-02-03
/dev/sda2 and /dev/sda5 both supposedly start on cylinder 32. According to [Wikipedia,]("http://en.wikipedia.org/wiki/Cylinder-head-sector#CHS_Addressing") the formula for translating from CHS to LBA is:

[IMG]http://upload.wikimedia.org/math/8/c/5/8c567aced00cd881691736fd37f5702e.png[/IMG]
[FONT=Verdana]
Plugging in the values from your fdisk output and assuming h and s values of 0, this [/FONT]means that the LBA (sector) address of cylinder 32 is:

A = (32 * 255 + 0) * 63 + 0 - 1 = 514,079

Thus, you'd try sector values near 514,079, but that are divisible by 16,065, 2048, or 63. For instance, you might try to start the partition on sector 514,080 (divisible by 16,065 and 63) or 514,048 (divisible by [noparse]2048)[/noparse] or 516,096 (also divisible by [noparse]2048).[/noparse] If these don't work, try moving forward and back by the suitable multiples.

I'd ignore the extended partition and just try to recover the LVM partition as a logical partition. Trying to recover the extended partition will just complicate matters, and it's unnecessary.

Good luck!

---

### Post by hodot on 2011-02-03
Ok, this is what being reported by TestDisk:

```
Disk /dev/rdisk0 - 750 GB / 698 GiB - CHS 1465149168 1 1, sector size=512
```

So can I safely assume my new layout would be:
```
/dev/sda1 = start 63, end 2016
/dev/sda2 = start 2017, end 1465144064
/dev/sda5 = start 2017, end 1465144064
```

?

Edited:
OK I just saw your posting, will try that first! Thanks!!

---

### Post by hodot on 2011-02-04
> Thus, you'd try sector values near 514,079, but that are divisible by 16,065, 2048, or 63. For instance, you might try to start the partition on sector 514,080 (divisible by 16,065 and 63) or 514,048 (divisible by 2048 ) or 516,096 (also divisible by 2048 ). If these don't work, try moving forward and back by the suitable multiples.

So basically I just use fdisk and delete the partition table and re-create based on what you have said above, right?

For example, I delete all the partition table and create partition 1 starts with 514,080 and end with the end of the sectors, which I believe is 1465149168 or 1465144064 and set the partition type to be 8e for Linux LVM, or just set it to Linux?

---

### Post by srs5694 on 2011-02-04
Yes, although if whatever's on /dev/sda1 is important, I'd just delete /dev/sda5 and /dev/sda2 rather than create a whole new partition table. Be aware you'll need to use fdisk in sector mode, so launch it with the "-u" switch ("sudo fdisk -u /dev/sda") or type "u" as the first command once it's launched.

---

### Post by hodot on 2011-02-04
I'm running OSX and I guess I can't use fdisk command shipped with OSX


```
bash-3.2# uname -a
Darwin xbmcs-Mac-mini.local 10.6.0 Darwin Kernel Version 10.6.0: Sun Jan  9 16:31:48 EST 2011; legacy kernel v6 :xnu-1504.9.26/BUILD/obj/RELEASE_I386 i386
bash-3.2# fdisk -h
fdisk: option requires an argument -- h
usage: fdisk [-ieu] [-f mbrboot] [-c cyl -h head -s sect] [-S size] [-r] [-a style] disk
        -i: initialize disk with new MBR
        -u: update MBR code, preserve partition table
        -e: edit MBRs on disk interactively
        -f: specify non-standard MBR template
        -chs: specify disk geometry
        -S: specify disk size
        -r: read partition specs from stdin (implies -i)
        -a: auto-partition with the given style
        -d: dump partition table
        -y: don't ask any questions
        -t: test if disk is partitioned
`disk' is of the form /dev/rdisk0.
auto-partition styles:
  boothfs     8Mb boot plus HFS+ root partition (default)
  bootufs     8Mb boot plus UFS root partition
  hfs         Entire disk as one HFS+ partition
  ufs         Entire disk as one UFS partition
  dos         Entire disk as one DOS partition
  raid        Entire disk as one 0xAC partition
bash-3.2#
``` 


Any idea which program should I use in OSX to re-partition that disk?

---

### Post by srs5694 on 2011-02-05
In principle, OS X's fdisk, or possibly diskutil, should work; however, I'm not familiar enough with either tool to give you specific instructions. Personally, I'd boot using [System Rescue CD]("http://www.sysresccd.org") or [Parted Magic]("http://partedmagic.com/doku.php") and use Linux's fdisk from there to do the job. That'll also have the advantage that you'll be able to use blkid to immediately determine whether your partition guesses are correct. A correct guess should produce something like this:

```
# **blkid /dev/sda1**
/dev/sda1: UUID="F0FYTX-mtb3-b8Kw-WZ3I-AhB6-JG3l-yCXWkA" TYPE="LVM2_member"

```If blkid returns nothing or says that the partition is something other than "LVM2_member", then you've defined it incorrectly. I don't believe you could do this from OS X.

If you can find your LVM data, you should then be able to use "vgchange -ay" to make the device files available under your rescue CD, so that you can check them out -- run fsck on them, etc.

---

### Post by hodot on 2011-02-05
FYI, this is what has been detected in TestDisk:

```
Results
   * FAT16 <32M                    32       8191       8160 [Hypervisor0]
     FAT16, 4177 KB / 4080 KiB
     FAT16 LBA                   8224     520191     511968 [Hypervisor1]
     FAT16, 262 MB / 249 MiB
     Linux                     502142 1442875773 1442373632
     EXT4 Large file Sparse superblock Backup superblock, 738 GB / 687 GiB
     FAT16 LBA                 520224    1032191     511968 [Hypervisor2]
     FAT16, 262 MB / 249 MiB
     FAT16 LBA                1257504    1843199     585696 [Hypervisor3]
     FAT16, 299 MB / 285 MiB
   P Linux Swap            1442875776 1465141615   22265840
     SWAP2 version 1, 11 GB / 10 GiB

```

These lines looks promising?

```
     Linux                     502142 1442875773 1442373632
     EXT4 Large file Sparse superblock Backup superblock, 738 GB / 687 GiB

```

But I was wondering shouldn't it detect as LVM2 or something?

---

### Post by srs5694 on 2011-02-05
It looks like you've found one of the logical volumes. You could try mounting it *read-only* to see what's there and then copy any data you want off of it. *Do not* mount it read/write or attempt to use fsck or other tools that might write to the partition/volume, though. As I wrote in post #4 in this thread, logical volumes can be discontiguous, and if this logical volume was discontiguous, writing to a partition that TestDisk recovers could damage data in other logical volumes.

---

### Post by hodot on 2011-02-05
I can't seems to mount it. Got some error regarding bad superblock. As what I understand from the TestDisk output, the superblock has somehow corrupted but there are still backup superblock, and the one that TestDisk found was in the backup superblock as well.

Here's the output from ubuntu livecd currently:
```
root@ubuntu:~# fdisk -ul /dev/sda

Disk /dev/sda: 750.2 GB, 750156374016 bytes
1 heads, 1 sectors/track, 1465149168 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x49e2fd2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          502142  1442875773   721186816   83  Linux
root@ubuntu:~# mount -t ext4 /dev/sda1 /media/test -o ro
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# mke2fs -n /dev/sda1
mke2fs 1.41.12 (17-May-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
45080576 inodes, 180296704 blocks
9014835 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
5503 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000

root@ubuntu:~#
```

Anyway, I tried setting the part to be 8e but running pvs and vgs shows nothing. blkid also shows nothing.

For the backup superblock, I've tried from 32768 until 1605632 but to no avail

---

### Post by hodot on 2011-02-05
This is another log from TestDisk:
```

recover_EXT2: "e2fsck -b 229376 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=7/5502, s_mnt_count=0/30, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 180296704
recover_EXT2: part_size 1442373632
     Linux                     502142 1442875773 1442373632
     EXT4 Large file Sparse superblock Backup superblock, 738 GB / 687 GiB
     Linux Swap            1442875776 1465141615   22265840
     SWAP2 version 1, 11 GB / 10 GiB
```

But when I tried:
```
root@ubuntu:~# e2fsck -b 229376 -B 4096 /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:~#
```

..

---

### Post by srs5694 on 2011-02-05
Then you're not likely to get anything from that. You could save the information so that you can re-create the partition later and run fsck on it if you get desperate, but for now I'd move on to other attempts, like trying to find the start of the physical volume (the LVM partition).

There was never any chance that you'd found the LVM partition; TestDisk would not have identified it as an ext4 filesystem if you had. In fact, in reviewing the TestDisk message again, it reports that it found a backup superblock. This suggests that the start of the filesystem may be earlier than what TestDisk reported. I don't know enough about either TestDisk or ext4fs to be sure of that, though, or to suggest how much earlier you should be looking for the start of the filesystem. I do know enough to realize that the fact that TestDisk only found a backup superblock is a bad sign; critical earlier data structures have probably been overwritten.

---

