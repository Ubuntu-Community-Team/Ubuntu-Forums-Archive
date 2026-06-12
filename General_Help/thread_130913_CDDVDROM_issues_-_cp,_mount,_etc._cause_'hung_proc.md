---
title: "CD/DVDROM issues - cp, mount, etc. cause 'hung process"
date: 2006-02-15
forum: General Help
---

### Post by Jave27 on 2006-02-15
(cross-posted from the 64-bit subforum because I don't think it's 64-bit exclusive and this one forum gets more traffic... sorry)

I've been having some problems recently with both my 16x DVDRW and my 40x CDRW drives.  They worked fine for a long time, and they still work in Windows, but recently things in Breezy have been acting up a bit.  While copying data from either drive (I thought it was just the DVD drive, but the CD drive has just started doing the same thing), occassionally it will just hang at a certain point.  It doesn't seem to matter which media, it's happened on numerous DVDs and CDs.  The entire system doesn't hang, but the cp/mv/mount/umount/eject routines will all hang.  Typing 'sudo kill -9 <pid>' will return, but it never actually kills the hung process.

/dev/hdd is my DVDRW drive, and /dev/hdc is my CDRW drive.

Here's my /etc/fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb1       /mnt/win32      ntfs    ro,user         0       0
/dev/hdb5       /mnt/win64      ntfs    ro,user         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/home           /chroot/home    none    bind            0       0
/tmp            /chroot/tmp     none    bind            0       0
/proc           /chroot/proc    proc    defaults        0       0
/dev            /chroot/dev     none    bind            0       0
/dev/hdc        /chroot/media/cdrom1    usd,iso9660     user,noauto     0      0/dev/hdd        /chroot/media/cdrom0    udf,iso9660     user,noauto     0      0
```

And here's some of my recent /var/kern.log entries that looked like they could be related to the problem:

```

Feb 14 09:25:32 localhost kernel: [ 4395.944700] ide: failed opcode was: unknownFeb 14 09:25:32 localhost kernel: [ 4395.944704] hdd: drive not ready for command
Feb 14 09:25:32 localhost kernel: [ 4395.944907] hdd: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 14 09:25:32 localhost kernel: [ 4395.944912] hdd: status error: error=0x04 { AbortedCommand }
Feb 14 09:25:32 localhost kernel: [ 4395.944915] ide: failed opcode was: unknownFeb 14 09:25:32 localhost kernel: [ 4395.944918] hdd: drive not ready for command
Feb 14 09:25:32 localhost kernel: [ 4395.945101] hdd: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 14 09:25:32 localhost kernel: [ 4395.945105] hdd: status error: error=0x04 { AbortedCommand }

Feb 14 09:57:43 localhost kernel: [ 6327.354491] hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x02)
Feb 14 09:58:43 localhost kernel: [ 6387.363355] hdd: lost interrupt
Feb 14 09:58:43 localhost kernel: [ 6387.363364] cdrom_pc_intr, write: dev hdd: flags = REQ_STARTED REQ_PC REQ_FAILED REQ_QUIET
Feb 14 09:58:43 localhost kernel: [ 6387.363369] sector 0, nr/cnr 0/0
Feb 14 09:58:43 localhost kernel: [ 6387.363372] bio 0000000000000000, biotail 0000000000000000, buffer 0000000000000000, data 0000000000000000, len 0
Feb 14 09:58:43 localhost kernel: [ 6387.363375] cdb: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Feb 14 09:58:43 localhost kernel: [ 6387.363381] hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x02)
Feb 14 09:59:43 localhost kernel: [ 6447.372245] hdd: lost interrupt
Feb 14 09:59:43 localhost kernel: [ 6447.372254] cdrom_pc_intr, write: dev hdd: flags = REQ_STARTED REQ_PC REQ_FAILED REQ_QUIET
Feb 14 09:59:43 localhost kernel: [ 6447.372259] sector 0, nr/cnr 0/0
Feb 14 09:59:43 localhost kernel: [ 6447.372262] bio 0000000000000000, biotail 0000000000000000, buffer 0000000000000000, data 0000000000000000, len 0
Feb 14 09:59:43 localhost kernel: [ 6447.372265] cdb: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Feb 14 09:59:43 localhost kernel: [ 6447.372271] hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x02)
```

Any ideas on what could be causing these issues, or how to really kill these processes?

---

### Post by Jave27 on 2006-03-03
*bump*

---

### Post by Jave27 on 2006-03-04
FYI - manually compiling & upgrading to the latest 2.6.15-5 vanilla kernel seems to have fixed these issues.

---

