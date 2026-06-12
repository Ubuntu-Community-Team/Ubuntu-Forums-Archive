---
title: "rebuild fstab"
date: 2009-12-23
forum: General Help
---

### Post by dgm8138 on 2009-12-23
Some inexperience led to the unintentional deletion of my /etc/fstab file.  I know that the computer will not boot properly without this file so I have been diligently trying to find a solution via google the past few days, but to no avail.  With that, I have signed up on the forums with the hope that someone can rebuild fstab for me, or least provide instructions on how to do so.

some info:
I do not have a backup of the file and I have not restarted/turned off the computer since the deletion of this file. 

ubuntu 9.04

sudo fdisk -l output is:

dan@dan-Not:~$ sudo fdisk -l
[sudo] password for dan: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x979c48fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26        7059    56492032   af  Unknown
/dev/sda3   *        7075       16863    78615975+   7  HPFS/NTFS
/dev/sda4           16863       19344    19932617+  83  Linux

I appreciate any help and if there is any more information needed just let me know

---

### Post by geirha on 2009-12-23
Shouldn't be a problem, but remember to do backups in the future!

Anyway, post the output of 
```

sudo blkid     # Shows the uuid of each filesystem
cat /etc/mtab  # Shows information on currently mounted filesystems, and mount options
# or, if mtab is gone too, the output of mount should suffice:
mount

```

---

### Post by dgm8138 on 2009-12-23
dan@dan-Not:~$ sudo blkid
[sudo] password for dan: 
/dev/sda1: LABEL="EFI" UUID="3F3C-1AF6" TYPE="vfat" 
/dev/sda2: UUID="83062D46C78FDD33" LABEL="Macintosh HD" TYPE="hfsplus" 
/dev/sda3: UUID="9A1C07811C075821" TYPE="ntfs" 
/dev/sda4: UUID="58e05acc-a255-48c7-ac8a-acbf5a7764c9" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="dc91869f-897e-47d1-a472-98551ae03fa5" 


dan@dan-Not:~$ cat /etc/mtab
/dev/sda4 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-17-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/dan/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=dan 0 0

thanks for the quick response and how would I go about a backup? just simply copy the contents of the file to a fstab.old?

---

### Post by geirha on 2009-12-23
This should be close to what you had before:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=58e05acc-a255-48c7-ac8a-acbf5a7764c9 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=dc91869f-897e-47d1-a472-98551ae03fa5 none swap defaults 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```

Backing up /etc and /home is a good idea. This explains some different ways to back up: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by dgm8138 on 2009-12-23
thank you i greatly appreciate your help with fstab and the backup references

---

