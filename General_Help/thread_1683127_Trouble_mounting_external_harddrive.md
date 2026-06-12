---
title: "Trouble mounting external harddrive"
date: 2011-02-07
forum: General Help
---

### Post by wess126 on 2011-02-07
Dear Ubuntu Users

I have a 320Gig external Hard drive that has, up until this morning, worked very well in both Win32 and Ubuntu 9.04. The problem began when I tried to access the contents this morning on XP and winexplorer asked if I wanted to format the drive, I selected no but then don't get access to the files. So I boot to Ubuntu and the drive does not appear on my desktop (usually there after +-30s after logging in). I tried manually with the following command and got

```
wroberts@wroberts-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/EXT/ -o uid=1000,gid=100,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I then had a look at dmesg | tail

```
wroberts@wroberts-desktop:~$ dmesg | tail
[  119.685609]  sdb: sdb1
[  119.710473] sd 9:0:0:0: [sdb] Attached SCSI disk
[  119.710540] sd 9:0:0:0: Attached scsi generic sg4 type 0
[  191.985346] mtrr: no MTRR for c0000000,10000000 found
[  500.769560] FAT: invalid media value (0x42)
[  500.769564] VFS: Can't find a valid FAT filesystem on dev sdb1.
[  819.863408] FAT: invalid media value (0x42)
[  819.863412] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 1216.524527] FAT: invalid media value (0x42)
[ 1216.524532] VFS: Can't find a valid FAT filesystem on dev sdb1.
```

fdisk -l returned the following which indicates that the file system is FAT32

```
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31b57b2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568640+   c  W95 FAT32 (LBA)

```

Am I missing something? I think there may be a problem with the external drive although I have not had it that long. My /etc/fstab looks like this

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=dc7ee3d7-1926-4f38-bc61-a8d7015668b9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=6c86da24-ab7b-4d02-b4e4-f2ac61b3ffdb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Any ideas on how I can rescue the data on the drive would be greatly appreciated.

Many thanks and kind regards,
Wesley**[B]**[/B]****

---

### Post by mikewhatever on 2011-02-07
Run a file system check on that partition in Windows. You seem to have file system errors, and hopefully, that should fix them.

---

