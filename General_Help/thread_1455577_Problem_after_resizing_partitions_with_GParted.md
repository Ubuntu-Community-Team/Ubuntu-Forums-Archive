---
title: "Problem after resizing partitions with GParted"
date: 2010-04-16
forum: General Help
---

### Post by krige on 2010-04-16
Hello,

I have resized some partitions using the GParted lice CD.

After the operations the following error appeared:

```
WARNING: the kernel failed to re-read the partition table on /dev/sda (device or resource busy). As a result, it may not reflect all of your changes after reboot.
```

I changed the size of one partition from 12GB to 120GB: the partition seemed to be resized as I wanted, but showed to have still 98% of used space.

After rebooting in the operating system GParted shows the same thing, the 120GB partition has 98% of used space, but Disk Usage Analyzer says the total filesystem capacity is 12GB.

This is the output of "sudo fdisk -lu":
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xec88ec88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    54540674    27270306    7  HPFS/NTFS
/dev/sda2       312367860   312576704      104422+  83  Linux
/dev/sda4        54540675   312367859   128913592+   5  Extended
/dev/sda5        54540738   303965864   124712563+  83  Linux
/dev/sda6       303965928   312367859     4200966   82  Linux swap / Solaris

Partition table entries are not in disk order
```

and this is the output of "sudo sfdisk -d":
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 54540612, Id= 7, bootable
/dev/sda2 : start=312367860, size=   208845, Id=83
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start= 54540675, size=257827185, Id= 5
/dev/sda5 : start= 54540738, size=249425127, Id=83
/dev/sda6 : start=303965928, size=  8401932, Id=82
```

Any idea on how I could fix this?

---

### Post by dcstar on 2010-04-16
> **krige said:**
> 
..........
Any idea on how I could fix this?

Do a fsck on it or a resize2fs.

---

### Post by krige on 2010-04-16
> **dcstar said:**
> Do a fsck on it or a resize2fs.

Thanks for the suggestion. I tried running "sudo fsck /dev/sda4" and this is what I have got:

```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?
```

---

### Post by john newbuntu on 2010-04-16
If what dcstar suggested does not work, run the command
sudo partprobe

If that does not fix issues, please post the outputs of:
cat /etc/fstab
sudo blkid -c /dev/null
sudo fdisk -l

---

### Post by krige on 2010-04-16
> **john newbuntu said:**
> If what dcstar suggested does not work, run the command
sudo partprobe

I only run fsck on sda2, 4, 5 and 6, all came out clean except 4 which produced  that "zero-length partition" message mentioned earlier.

sudo partprobe didn't have any effect, and no output at all. Running it with the -s option produced this:

```
/dev/sda: msdos partitions 1 4 <5 6> 2
```

**cat /etc/fstab**
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=a1f57803-f87b-45ee-b76a-b6ff4eb32271 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ad6d4b9e-9426-452a-b08e-ff26a046333f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

**sudo blkid -c /dev/null**
```
/dev/sda1: UUID="E8A0B2D5A0B2AA08" TYPE="ntfs" 
/dev/sda2: LABEL="/boot" UUID="ce52462f-f57f-4b2a-a21b-81bbca9957fc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="a1f57803-f87b-45ee-b76a-b6ff4eb32271" TYPE="ext4" 
/dev/sda6: UUID="ad6d4b9e-9426-452a-b08e-ff26a046333f" TYPE="swap" 
```

**sudo fdisk -l**
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xec88ec88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3395    27270306    7  HPFS/NTFS
/dev/sda2           19445       19457      104422+  83  Linux
/dev/sda4            3396       19444   128913592+   5  Extended
/dev/sda5            3396       18921   124712563+  83  Linux
/dev/sda6           18922       19444     4200966   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Mark Phelps on 2010-04-16
Did you notice that sda4 is an Extended partition?  That's not an actual partition, instead, it's a holder for other partitions -- so of course, you can't run fsck on it.

---

### Post by john newbuntu on 2010-04-17
Can you please post the output of:
df -Th

---

### Post by krige on 2010-04-19
> **john newbuntu said:**
> Can you please post the output of:
df -Th

```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext4     13G  9.6G  2.2G  82% /
none      devtmpfs    2.0G  268K  2.0G   1% /dev
none         tmpfs    2.0G  1.8M  2.0G   1% /dev/shm
none         tmpfs    2.0G  424K  2.0G   1% /var/run
none         tmpfs    2.0G     0  2.0G   0% /var/lock
none         tmpfs    2.0G     0  2.0G   0% /lib/init/rw
```

---

### Post by krige on 2010-04-22
Any clue?

---

### Post by krige on 2010-04-26
Rebooting in GParted Live and running "Partition / Check" did fix the problem. I have never imagined it could have been so easy.

---

