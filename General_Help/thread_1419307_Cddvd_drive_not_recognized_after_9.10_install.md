---
title: "Cd/dvd drive not recognized after 9.10 install"
date: 2010-03-01
forum: General Help
---

### Post by cwfrad on 2010-03-01
I recently upgraded from 9.04 to 9.10 and now my cd/dvd-r drive doesn't exist. When I run sudo lshw -c disk command I get

*-disk                  
       description: ATA Disk
       product: WDC WD1600AAJB-5
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 58.0
       serial: WD-WCAS2A368839
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000006b
  *-cdrom:0
       description: DVD-RAM writer
       product: DVD Writer 1040r
       vendor: HP
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: MH21
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM SD-616F
       vendor: SAMSUNG
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: F100
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       size: 1910MiB (2003MB)
       capabilities: partitioned partitioned:dos
       configuration: signature=2fd96f60

It shows all my drives (including the little usb flash drive) but I can't get to the drives from "computer" all it shows is cdrom0 floppy0 and filesystem

---

