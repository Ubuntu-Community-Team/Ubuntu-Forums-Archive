---
title: "Flash drive not being recognized"
date: 2006-02-16
forum: General Help
---

### Post by Piggah on 2006-02-16
Hi,

I'm having a problem. Suddenly, my flash drive is not being recognized when I plug it in. I tried to mount it, but it says it cant find a file system. Here's my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda1       /windows     ntfs    nls=utf8,umask=0222        0       0
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0

```

Not sure what to do with this. 

Thanks in advance.

---

### Post by o_fortuna on 2006-02-16
[QUOTE=Piggah]Hi,

I'm having a problem. Suddenly, my flash drive is not being recognized when I plug it in. I tried to mount it, but it says it cant find a file system. Here's my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda1       /windows     ntfs    nls=utf8,umask=0222        0       0
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0

```

Not sure what to do with this. 

Thanks in advance.[/QUOTE]
Put this in the terminal (Applications-->Accessories-->Terminal):
```
dmesg|tail
```
and post the output here. That will generally show any errors you have. For example, when I plug in a USB drive, I get
```
~$ dmesg|tail
[4469745.340000] sdb: Mode Sense: 03 00 00 00
[4469745.340000] sdb: assuming drive cache: write through
[4469745.346000] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[4469745.348000] sdb: Write Protect is off
[4469745.348000] sdb: Mode Sense: 03 00 00 00
[4469745.348000] sdb: assuming drive cache: write through
[4469745.348000]  /dev/scsi/host4/bus0/target0/lun0: p1
[4469745.349000] Attached scsi removable disk sdb at scsi4, channel 0, id 0, lun 0
[4469745.350000] usb-storage: device scan complete
[4469745.827000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

---

### Post by Piggah on 2006-02-16
```
nick@nick:~$ dmesg|tail
[4472515.168000] SCSI error : <6 0 0 0> return code = 0x70000
[4472515.168000] end_request: I/O error, dev sdb, sector 82000
[4472515.168000] SCSI error : <6 0 0 0> return code = 0x70000
[4472515.168000] end_request: I/O error, dev sdb, sector 82001
[4472515.168000] SCSI error : <6 0 0 0> return code = 0x70000
[4472515.168000] end_request: I/O error, dev sdb, sector 82002
[4472515.168000] SCSI error : <6 0 0 0> return code = 0x70000
[4472515.168000] end_request: I/O error, dev sdb, sector 82003
[4472515.169000] SCSI error : <6 0 0 0> return code = 0x70000
[4472515.169000] end_request: I/O error, dev sdb, sector 82004

```

---

### Post by o_fortuna on 2006-02-16
[QUOTE=Piggah]```
nick@nick:~$ dmesg|tail
[4472515.168000] SCSI error : <6 0 0 0> return code = 0x70000
[4472515.168000] end_request: I/O error, dev sdb, sector 82000
[4472515.168000] SCSI error : <6 0 0 0> return code = 0x70000
[4472515.168000] end_request: I/O error, dev sdb, sector 82001
[4472515.168000] SCSI error : <6 0 0 0> return code = 0x70000
[4472515.168000] end_request: I/O error, dev sdb, sector 82002
[4472515.168000] SCSI error : <6 0 0 0> return code = 0x70000
[4472515.168000] end_request: I/O error, dev sdb, sector 82003
[4472515.169000] SCSI error : <6 0 0 0> return code = 0x70000
[4472515.169000] end_request: I/O error, dev sdb, sector 82004

```[/QUOTE]
Hm, I wonder if it's related to the computer or the flash disk itself. Have you tried plugging the drive into another computer (or, even better, the same computer with a different OS/live CD) where it worked? If it doesn't work anywhere else, it might be broken, though I doubt that's the case. Also, do any other USB devices (iPod, etc.) work?

---

### Post by Piggah on 2006-02-16
Hmm, well, it seems to have magically fixed itself after a reboot.

The only problem I'm facing now is that nothing is being written to the drive. I copy it on, but it's not there after I try to access it again. =\

---

