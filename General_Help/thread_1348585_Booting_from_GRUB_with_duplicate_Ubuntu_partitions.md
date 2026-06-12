---
title: "Booting from GRUB with duplicate Ubuntu partitions"
date: 2009-12-07
forum: General Help
---

### Post by Quatrix on 2009-12-07
[FONT="Verdana"]

I have two identical hard drives and use the second as a backup.  Occasionally I use Acronis to clone the master to the backup.

Recently, after installing Windows 7 and restoring GRUB, it boots into the backup Ubuntu partition instead of the master.  Could someone please take a look at this info and see what's going wrong?  Notice that because I directly clone the drive, the master and backup UBUNTU partitions (sda1 and sdb3) have the same UUID.

blkid:

```
/dev/sda1: LABEL="UBUNTU" UUID="06a13bf6-c4ae-f755-da77-b640bdf8e014" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda4: UUID="B618091A1808DAEF" LABEL="WIN7" TYPE="ntfs" 
/dev/sda5: UUID="F49DF398D8040E7A" LABEL="WINXP" TYPE="ntfs" 
/dev/sda6: UUID="5EC5D08AC339802B" LABEL="GAMES" TYPE="ntfs" 
/dev/sda7: UUID="32EFEEBEB5D2EF94" LABEL="DATA" TYPE="ntfs" 
/dev/sda8: UUID="2A5306AA8A44DF6E" LABEL="TEMP" TYPE="ntfs" 
/dev/sdb1: UUID="3B7B1E941EEFDE49" LABEL="MAIN" TYPE="ntfs" 
/dev/sdb3: LABEL="UBUNTU" UUID="06a13bf6-c4ae-f755-da77-b640bdf8e014" TYPE="ext3" 
/dev/sdb5: UUID="F49DF398D8040E7A" LABEL="WINDOWS" TYPE="ntfs" 
/dev/sdb6: UUID="5EC5D08AC339802B" LABEL="GAMES" TYPE="ntfs" 
/dev/sdb7: UUID="32EFEEBEB5D2EF94" LABEL="MEDIA" TYPE="ntfs" 
/dev/sdb8: UUID="2A5306AA8A44DF6E" LABEL="TEMP" TYPE="ntfs" 

```

```
fdisk:

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc566bf2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6166    49528363+  83  Linux
/dev/sda3           19222      182401  1310743350    5  Extended
/dev/sda4   *        6167       19221   104864286    7  HPFS/NTFS
/dev/sda5           19222       32276   104864250+   7  HPFS/NTFS
/dev/sda6           32277      136711   838874100+   7  HPFS/NTFS
/dev/sda7          136712      177179   325059163    7  HPFS/NTFS
/dev/sda8          177180      182401    41945683+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35dd0d61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        6167       19221   104864287+  17  Hidden HPFS/NTFS
/dev/sdb2           19222      182401  1310743350    5  Extended
/dev/sdb3               1        6166    49528363+  83  Linux
/dev/sdb5           19222       32276   104864256   17  Hidden HPFS/NTFS
/dev/sdb6           32277      136710   838866073+  17  Hidden HPFS/NTFS
/dev/sdb7          136711      175873   314576766   17  Hidden HPFS/NTFS
/dev/sdb8          175874      182401    52436128+  17  Hidden HPFS/NTFS

Partition table entries are not in disk order
```

fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1
#UUID=06a13bf6-c4ae-f755-da77-b640bdf8e014 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/mnt/swap  none  swap  sw  0 0
```

menu.lst:

```
title		Ubuntu 9.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=06a13bf6-c4ae-f755-da77-b640bdf8e014 ro quiet splash
initrd		/boot/initrd.img-2.6.28-15-generic
quiet
```

[/FONT]

---

### Post by oldfred on 2009-12-07
I am surprised you are even able to boot with the duplicate UUIDs. I have seen several cases where it just will not boot with two UUIDs the same.

I would change all entries in fstab and menu.lst to the less preferred root and sda= rather than have any entries using UUIDs.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

In menu.lst is this stanza, I have UUID set change to the root=/dev/hda1 style ) I do not know if it is hda1 or sda1 now?

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. [COLOR=DarkRed]kopt=root=/dev/hda1 ro[/COLOR]
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f9b2a783-78ba-4437-9bc5-9d8cfa86ff0c ro

---

### Post by Quatrix on 2009-12-07
Weird.  I just tried again (I think) without changing anything, and it booted into the correct (master) partition.  I changed the GRUB entries to use /dev/sda1 instead of the UUID just in case, and it's still working.  Thanks.

---

