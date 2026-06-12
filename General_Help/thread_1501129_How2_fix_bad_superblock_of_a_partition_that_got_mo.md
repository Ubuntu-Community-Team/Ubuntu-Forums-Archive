---
title: "How2: fix bad superblock of a partition that got moved with Gparted"
date: 2010-06-03
forum: General Help
---

### Post by Browser_ice on 2010-06-03
Tonight I did a bit of cleanup amongst my partitions of my 2nd HD. The last thing I did was moving an ext3 partition to the left over a hudge gap I had cleaned up.  That partition was a filesystem on the 2nd hd pointed to by my ubuntu 8.04 (on 1st hd).  I had umounted all partitions prior to this.

After the move was done, gparted failed on the last step  "e2fsck -f -y -v /dev/sdb6" saying :

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap of ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>.

See attached txt file for the complete work gparted did on that partition.

I tried that "e2fsck -b 8193 <device>" but it gave me the same error:
~$ sudo e2fsck -b 8193 /dev/sdb6
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: No such file or directory while trying to open /dev/sdb6

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


How do I fix this partition without loosing the data on it ?

[added comments on stuff I read and try]

~$ sudo mke2fs -n /dev/sdb6
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/sdb6 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

> sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28842883

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1957    15719571    7  HPFS/NTFS
/dev/sda2            1958        9963    64308195    f  W95 Ext'd (LBA)
/dev/sda5            7353        9963    20972857+  83  Linux
/dev/sda6            1959        4741    22354416   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000782bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         522     4192933+  82  Linux swap / Solaris
/dev/sdb2             523        4439    31457280+   7  HPFS/NTFS
/dev/sdb3            4440        5221     6281415    b  W95 FAT32
/dev/sdb4            5222       30515   203174055    f  W95 Ext'd (LBA)
/dev/sdb5            5222        8354    25165791    7  HPFS/NTFS
/dev/sdb6            8355       20468    97305673+  83  Linux

~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              20G  3.2G   16G  17% /
varrun               1014M  116K 1014M   1% /var/run
udev                 1014M   76K 1014M   1% /dev
devshm               1014M   92K 1014M   1% /dev/shm


---

### Post by BoneKracker on 2010-06-03
Try 'sudo partprobe' (which will force the kernel to re-read the partition table), or reboot if you can't do that.

You _might_ then be able to proceed with your plan to use 'mke2fs -n' to identify a non-corrupt superblock, which you can then use to assist fsck in repairing the filesystem.

---

### Post by Browser_ice on 2010-06-03
I have just rebooted. At first glance, gparted sees my /dev/sdb6. I am doing a check on it right now ..  I'll come back in 5-10 min with the results of your suggestions.


Ok the CHecked says its ok. I mounted it and I am able to list its content. So it looks like its ok. I guess because of all the things I did in Gparted, it needed a reboot to replace my /dev/sdb6 ?

---

