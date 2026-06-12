---
title: "cdrom drive not recognised"
date: 2011-10-03
forum: General Help
---

### Post by jamessfc on 2011-10-03
I have a problem with my CDrom drive now not recognised after rebooting from a USB. The drive shows up in BIOS setting but not in the BootMenu. In terminal the following:
sudo lshw -c disk

  *-disk                  
       description: ATA Disk
       product: MAXTOR STM325031
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 6RY3R085
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000918ab
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=eef844d8


and I am unable to mount:
sudo mount/dev/dvd/cdrom
sudo: mount/dev/dvd/cdrom: command not found


Any suggestions??

---

### Post by sum1nil on 2011-10-03
I believe your cd's/dvd's are listed in /dev as srX so the command would be like: mount -t iso9660 /dev/sr0 /media/dvd

You must make the directory /media/dvd beforehand.



Hope this helps.
:popcorn:

---

