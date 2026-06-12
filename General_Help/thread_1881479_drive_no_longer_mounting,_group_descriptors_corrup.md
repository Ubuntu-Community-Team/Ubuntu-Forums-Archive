---
title: "drive no longer mounting, group descriptors corrupted"
date: 2011-11-15
forum: General Help
---

### Post by illuminate1 on 2011-11-15
Hi all, new user here. I did my due diligence and tried to find the answer prior to posting and have tried a few things but I am still broken. My situation: I have a storage device hooked up to a Ubuntu server via iSCSI. I had it all talking nicely and up and running about 2 weeks ago. Now the device will now longer mount. 

```
root@Backup:~# mount /backups2
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

The log..
```
root@Backup:~# dmesg | tail
[   39.995906] sd 2:0:0:1: [sdb] 18556198912 512-byte logical blocks: (9.50 TB/8.64 TiB)
[   39.998644] sd 2:0:0:1: [sdb] Write Protect is off
[   39.998654] sd 2:0:0:1: [sdb] Mode Sense: 97 00 00 08
[   40.000292] sd 2:0:0:1: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.003415]  sdb: sda1
[   40.018085] sd 2:0:0:0: [sda] Attached SCSI disk
[   40.026415]  unknown partition table
[   40.030556] sd 2:0:0:1: [sdb] Attached SCSI disk
[ 5715.244441] EXT4-fs (sda1): ext4_check_descriptors: Checksum for group 0 failed (51749!=0)
[ 5715.244453] EXT4-fs (sda1): group descriptors corrupted!
```

Did some research and found this [link]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/") and tried the following:

```
root@Backup:~# fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Group descriptors look bad... trying backup blocks...
fsck.ext4: Bad magic number in super-block when using the backup blocks
fsck.ext4: going back to original superblock
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

root@Backup:~# mke2fs -n /dev/sda1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
549363712 inodes, 2197444096 blocks
109872204 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
67061 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848, 512000000, 550731776, 644972544, 1934917632

root@dvoBackupserver01:~# e2fsck -b 1605632 /dev/sda1
/dev/sda1 contains a file system with errors, check forced.
Resize inode not valid.  Recreate<y>? yes

Pass 1: Checking inodes, blocks, and sizes
yyyInode 425 has a extra size (65535) which is invalid
Fix<y>? yes

Inode 426 is in use, but has dtime set.  Fix<y>? yes

Inode 426 has a extra size (18635) which is invalid
Fix<y>? yes

Inode 426 has compression flag set on filesystem without compression support.  Clear<y>? yes

Inode 426, i_size is 6414028916418760925, should be 0.  Fix<y>? yes

Inode 426, i_blocks is 6779278794416, should be 0.  Fix<y>? yes

Inode 427 is in use, but has dtime set.  Fix<y>? yes

Inode 427 has a extra size (42746) which is invalid
Fix<y>? yes

Inode 428 is in use, but has dtime set.  Fix<y>? yes

Inode 428 has imagic flag set.  Clear<y>? yes

Inode 428 has a extra size (11520) which is invalid
Fix<y>? yes

Inode 429 is in use, but has dtime set.  Fix<y>?
```

The above errors just went on and on.. Can anyone guide me in the next steps? I can provide more information as needed, please help!

---

### Post by illuminate1 on 2011-11-15
```
root@Backup:/# fdisk -ul /dev/sda1

Disk /dev/sda1: 9000.7 GB, 9000731017216 bytes
255 heads, 63 sectors/track, 1094276 cylinders, total 17579552768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table
```

Can anyone help with this issue? I am truly at a loss.

---

### Post by illuminate1 on 2011-11-16
Bumping up, again.

---

### Post by LewisTM on 2011-11-16
Try installing and running testdisk. This utility will read the disk and try to find lost partitions, then rebuild the table. Run a deep check and identify the partition(s) you would like to recover.

You can then run 'fsck.ext4 -f' on the recovered partition.

I've recently had trouble with an ext4 partition that kept getting corrupted. Switched to JFS, so far so good. I suggest you do the same if the problem recurs.

Good luck!

---

### Post by illuminate1 on 2011-11-16
Thank you for the direction.. As I am very new, how would I install testdisk, apt-get testdisk?

---

### Post by LewisTM on 2011-11-16
> **illuminate1 said:**
> Thank you for the direction.. As I am very new, how would I install testdisk, apt-get testdisk?
```
sudo apt-get install testdisk
```
then launch it with ```
sudo testdisk
```

You can can also try installing gpart and gparted
```
sudo apt-get install gpart gparted
```
then launch with ```
sudo gparted
```. Switch to you SCSI disk and pick the 'Device/Attempt data rescue' menu item. Although that didn't work for me...

---

### Post by illuminate1 on 2011-11-16
Thank you again. When I try I get the following (sorry so needy!): 

```
root@Backup:~# apt-get install testdisk
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ifstat: Depends: libsnmp4.2 but it is not installable
          Depends: libssl0.9.6 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@Backup:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ifstat
The following packages will be upgraded:
  ifstat
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 21.8kB of archives.
After this operation, 4,096B of additional disk space will be used.
E: You don't have enough free space in /var/cache/apt/archives/.

```

---

### Post by LewisTM on 2011-11-16
Looks like you have a broken ifstat package for some unknown reason.
This should not affect testdisk.
Try to install it again and run it.
Also the out of space message is worrisome. You should run 'apt-get clean' to make some room.

---

### Post by illuminate1 on 2011-11-16
I ran apt-get clean
```
root@Backup:~# apt-get clean

```

Then tried the install again, but again with the dependencies error: 
```
root@Backups:~# apt-get install testdisk
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ifstat: Depends: libsnmp4.2 but it is not installable
          Depends: libssl0.9.6 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@dvoBackupserver01:~# testdisk
The program 'testdisk' is currently not installed.  You can install it by typing:
apt-get install testdisk

```

So my install isn't working. :confused:

---

### Post by LewisTM on 2011-11-16
This is annoying.
You can either apt-get remove ifstat to get rid of the problem, or use some other package manager that will offer as solution, such as aptitude or synaptic or even Software Center.
Then you can proceed with installing new stuff.

---

### Post by illuminate1 on 2011-11-16
> **LewisTM said:**
> This is annoying.
You can either apt-get remove ifstat to get rid of the problem, or use some other package manager that will offer as solution, such as aptitude or synaptic or even Software Center.
Then you can proceed with installing new stuff.


I totally agree! I am looking into aptitude now.

---

