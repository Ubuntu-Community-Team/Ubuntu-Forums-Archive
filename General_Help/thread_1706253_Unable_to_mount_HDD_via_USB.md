---
title: "Unable to mount HDD via USB"
date: 2011-03-13
forum: General Help
---

### Post by SaintBasil on 2011-03-13
I am unable to mount any device with a hard drive in it via USB. I tried an external HDD, and a Sony Walkman. Both devices mounted fine on my Windows partition and on a separate Ubuntu PC, o I know they are not the problem. I get the following error:


```
Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

My dmesg tail is:

```
[ 1961.483852] sd 6:0:0:0: Attached scsi generic sg1 type 0
[ 1961.496579] sd 6:0:0:0: [sdb] 625142447 512-byte logical blocks: (320 GB/298 GiB)
[ 1961.498946] sd 6:0:0:0: [sdb] Write Protect is off
[ 1961.498958] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1961.498966] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1961.504210] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1961.504227]  sdb: sdb1
[ 1961.521959] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1961.521986] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 1961.989601] UDF-fs: No anchor found
[ 1961.989616] UDF-fs: Rescanning with blocksize 2048
[ 1962.050486] UDF-fs: No anchor found
[ 1962.050499] UDF-fs: No partition found (1)
[ 1962.107869] ISOFS: Unable to identify CD-ROM format.
[ 1962.226480] UDF-fs: No anchor found
[ 1962.226492] UDF-fs: Rescanning with blocksize 2048
[ 1962.252120] UDF-fs: No anchor found
[ 1962.252130] UDF-fs: No partition found (1)
[ 1962.307501] ISOFS: Unable to identify CD-ROM format.
[ 1965.371247] usb 1-4: USB disconnect, address 5

```

Finally, my fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=cb317c09-34cf-417d-be28-fc816d394b0d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=7473fce0-dcec-4f10-bfdc-a47b173dcb47 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Anyone understand what the problem is?

---

### Post by kanikilu on 2011-03-14
According to the information you gave, /dev/sdb1 is the CD-ROM drive. Why are you trying to mount an external hard-drive using that device name?

Plug in the hard-disk and see what the device name is with ```
sudo fdisk -l
```

Also, is /dev/sdb1 in fact the correct device name for the CD-ROM? Maybe it's wrong in fstab? Try to find out more information about the CD-ROM...for example: ```
sudo lshw | grep -A15 "*-cdrom"
```

---

### Post by Kilz on 2011-03-23
The computer is assuming that any devive assined to sdc is a cdrom because of the fstab entry. To fix it I would sugest this replacement.
First open it as an admin to edit the file
```
sudo gedit /etc/fstab
```

Then change the line to read

```
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

if you have any other cdrom's the following line would add a number like this.

```
/dev/cdrom1       /media/cdrom1   udf,iso9660 user,noauto     0       0
```

You may get an error until you reboot when loading things via usb or cdrom, so reboot.

---

