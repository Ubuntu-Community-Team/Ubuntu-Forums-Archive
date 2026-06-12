---
title: "unable to mount location timeout by message bus"
date: 2010-01-31
forum: General Help
---

### Post by createsean on 2010-01-31
I've got ubuntu 9.10 installed and can access all partitions on my 3 drives except for one. When I try to access this partition I get the following error:

"Unable to mount location
Message did not receive reply (timeout by message bus)"

for the record this is a 805mb partition on a 1.5TB drive.

I'm a complete novice and would appreciate all help.

---

### Post by john newbuntu on 2010-01-31
To start with, open up a terminal (Applications->accessories->terminal), type the following commands and post the outputs please:
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
cat /proc/mounts

```

---

### Post by createsean on 2010-01-31
Thank you for your help.


sudo fdisk -l
output
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2cee2cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           14167       27424   106494885    5  Extended
/dev/sda2   *           1       14166   113788362+   7  HPFS/NTFS
/dev/sda3           27425       60801   268100752+   7  HPFS/NTFS
/dev/sda5           14167       26879   102117141   83  Linux
/dev/sda6           26880       27424     4377681   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49ee32d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2       22544   181076616    7  HPFS/NTFS
/dev/sdb6           22545       60801   307299321    7  HPFS/NTFS
omitting empty partition (5)

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d60f450

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2      182401  1465128000    f  W95 Ext'd (LBA)
/dev/sdc5               2       97909   786445978+   7  HPFS/NTFS
/dev/sdc6           97910      182401   678681958+   7  HPFS/NTFS


sudo blkid output
> /dev/sda2: UUID="12F8B5DEF8B5C071" TYPE="ntfs" 
/dev/sda3: UUID="0A2604D82604C723" LABEL="Other Media" TYPE="ntfs" 
/dev/sda5: UUID="c258c6db-10f4-4d92-b45e-5410391ebc32" TYPE="ext4" 
/dev/sda6: UUID="ee31752a-e951-4cae-af24-0acdbf53190f" TYPE="swap" 
/dev/sdb5: UUID="3C90E58C90E54D48" LABEL="Miscellaneous" TYPE="ntfs" 
/dev/sdb6: UUID="50481A114819F686" LABEL="Storage" TYPE="ntfs" 
/dev/sdc5: UUID="26FACF2CFACEF6D9" LABEL="Vid-editing" TYPE="ntfs" 
/dev/sdc6: UUID="868AE5BB8AE5A83F" LABEL="Media" TYPE="ntfs"


cat /etc/fstab output
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=c258c6db-10f4-4d92-b45e-5410391ebc32 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ee31752a-e951-4cae-af24-0acdbf53190f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
sean@sean-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=c258c6db-10f4-4d92-b45e-5410391ebc32 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ee31752a-e951-4cae-af24-0acdbf53190f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


cat /proc/mounts output

> rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev tmpfs rw,relatime,mode=755 0 0
/dev/disk/by-uuid/c258c6db-10f4-4d92-b45e-5410391ebc32 / ext4 rw,relatime,errors=remount-ro,barrier=1,data=ordered 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/sean/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0


---

### Post by john newbuntu on 2010-01-31
I guess you are not able to access /dev/sdc5.  Try mounting it manually as follows using the terminal:

```
sudo mkdir /mnt/vid
sudo mount  -t ntfs-3g /dev/sdc5 /mnt/vid
```

If this succeeds, open nautilus and try to access the files in /mnt/vid

---

### Post by createsean on 2010-02-01
I typed those commands in terminal and didn't get any error messages. However I can't find nautilus under the applications or system menu.

---

### Post by john newbuntu on 2010-02-01
Click on places->computer.  Are you able to see the 805 mb Filesystem?

---

### Post by createsean on 2010-02-03
I was able to see it previously but got an error. Now it's not there at all.

---

