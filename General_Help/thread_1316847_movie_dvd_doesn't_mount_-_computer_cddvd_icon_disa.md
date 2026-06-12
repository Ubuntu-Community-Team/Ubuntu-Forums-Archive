---
title: "movie dvd doesn't mount - computer cd/dvd icon disappears"
date: 2009-11-06
forum: General Help
---

### Post by pavloukos on 2009-11-06
Hi, I have a strange case here. I am currently running ubuntu 9.10.
Whenever I insert a movie dvd, nothing gets mounted (even dvd's I've made with devede on ubuntu) and the cd/dvd icon from computer:/// places disappears. 

Trying to mount it manually, I get:
```
paul@paul-desktop:~$ sudo mount /dev/dvd
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

The syslog erros are:


```
Nov  6 16:32:48 paul-desktop kernel: [ 1516.364167] attempt to access beyond end of device
Nov  6 16:32:48 paul-desktop kernel: [ 1516.364173] sr0: rw=0, want=68, limit=4
Nov  6 16:32:48 paul-desktop kernel: [ 1516.364177] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
Nov  6 16:32:48 paul-desktop kernel: [ 1516.370966] attempt to access beyond end of device
Nov  6 16:32:48 paul-desktop kernel: [ 1516.370970] sr0: rw=0, want=68, limit=4
Nov  6 16:32:48 paul-desktop kernel: [ 1516.375175] attempt to access beyond end of device
Nov  6 16:32:48 paul-desktop kernel: [ 1516.375178] sr0: rw=0, want=1028, limit=4
Nov  6 16:32:48 paul-desktop kernel: [ 1516.375762] attempt to access beyond end of device
Nov  6 16:32:48 paul-desktop kernel: [ 1516.375765] sr0: rw=0, want=2052, limit=4
Nov  6 16:32:48 paul-desktop kernel: [ 1516.375768] UDF-fs: No anchor found
Nov  6 16:32:48 paul-desktop kernel: [ 1516.375770] UDF-fs: No partition found (1)
```

My fstab is:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc2 during installation
UUID=d589735f-f43c-4e79-b776-4a94eb4fe389 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=477d8093-4164-48e6-93e2-60d770d44ead /home           ext4    defaults        0       2
# swap was on /dev/sdc1 during installation
UUID=a10ea809-3932-405c-a323-2a593cd23cb0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0
```

Finally, lshw gives:
```

paul@paul-desktop:~$ sudo lshw -c disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD_RW ND-4571A
       vendor: _NEC
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1-01
       serial: [_NEC    DVD_RW ND-4571A 1-0106011700
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-disk:0
       description: ATA Disk
       product: HDS728080PLA380
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: PF2O
       serial: PFDB32E8S3ZM8M
       size: 76GiB (82GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b56fa37b
  *-disk:1
       description: ATA Disk
       product: SAMSUNG SP2504C
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: VT10
       serial: S09QJ1DL701274
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d430d430
  *-disk
       description: ATA Disk
       product: Hitachi HDS72101
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: GKAO
       serial: GTA001PBG3KE8G
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000be836
  *-disk
       description: SCSI Disk
       product: Photosmart C3180
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdd
       version: 1.00
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sde
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=1a37dfb9

```



Can someone please help? This is really annoying. Just for the record, data dvd's open up fine.

---

### Post by drrakken on 2009-11-06
You may need to enable restricted extras

---

### Post by HiImTye on 2009-11-06
> **drrakken said:**
> You may need to enable restricted extras
likely the case as copy protected DVDs wont let you mount them without it

---

### Post by pavloukos on 2009-11-06
Thanks for replying.

It's not that. ubuntu-restricted-extras are already installed :(
i've also added vlc and the output gives:

```

[0x97f71c8] main interface error: no interface module matched "globalhotkeys,none"
[0x97f71c8] main interface error: no suitable interface module
[0x9682140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9682140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: disc is unscrambled
libdvdcss error: seek error
libdvdcss error: seek error
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdcss error: seek error
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: disc is unscrambled
libdvdcss error: seek error
libdvdcss error: seek error
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdcss error: seek error
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[0x99978b8] main access error: no access module matched "dvd"
[0xb66009d8] main input error: open of `dvd://' failed: no access module matched "dvd"
libdvdnav: Using dvdnav version 4.1.3
libdvdnav: Can't seek to block 32
libdvdnav: Unable to find map file '/home/paul/.dvdnav/.map'
libdvdnav: vm: failed to read VIDEO_TS.IFO

```

---

### Post by pavloukos on 2009-11-07
It turned out that it was a hw problem with my old scsi drive. As soon as I replaced it with a new sata dvd drive everything was back to normal.

---

### Post by mjitkop on 2009-11-09
Very interesting because I am having exactly the same problem. I have tried all combinations of master/slave (with my hard drive) on both IDE1 and IDE2 with the same results.

I will try replacing the (old) DVD-ROM drive to see if it makes a difference. ;)

---

### Post by RockinRob2258 on 2009-11-10
> **pavloukos said:**
> It turned out that it was a hw problem with my old scsi drive. As soon as I replaced it with a new sata dvd drive everything was back to normal.

I have an older dvd drive and similar problem to the original poster.  I don't think that buying a SATA dvd drive is a good option for me since, well...there are no SATA adapters on my seven year old motherboard.

I noticed that in the original poster's fstab file, he has the noauto option on his optical drives.  I looked in my fstab file and found the same thing.  I changed noauto to auto, rebooted and everything worked just fine.  The disk mounted automatically upon insertion.

Contents of old fstab file:

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
UUID=893000af-285a-4d8c-b73b-f02fc0d26a89 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=16c71e1b-0620-4d52-91eb-8c10b185bf0b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```Edited fstab file that now works:```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=893000af-285a-4d8c-b73b-f02fc0d26a89 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=16c71e1b-0620-4d52-91eb-8c10b185bf0b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,auto,exec,utf8 0       0
```

---

### Post by RockinRob2258 on 2009-11-10
Now if I could get it to eject the dvd...

---

### Post by pavloukos on 2009-11-10
doesn't the eject command work for you?

Furthermore, after I installed the new drive, neither brasero nor gnomebaker could successfully burn a dvd. However k3b works fine ... weird!

---

### Post by mjitkop on 2010-01-04
Sorry to resurrect this 2-month old thread but I thought you may find this interesting: without making any changes whatsoever to the hardware, I replaced Ubuntu 9.10 with Ubuntu 9.04 and the DVD drive works fine! I will be keeping 9.04 on it.

---

