---
title: "cd/dvdrom drive issue Lucid Lynx"
date: 2010-05-24
forum: General Help
---

### Post by cinemageek on 2010-05-24
To the wonderful people at ubuntu forums,

I need help with my cd/dvd drive. I think the problem is the symbolic links but I am not completely sure. The drive is detected and it seems to mount on my gui home window, I am also able to open the disk that is in the drive within my nautilus file browser or whatever it may be. I am running ubuntu lucid lynx 10.04 and everything else seems to be working fine. I will post whatever information you need to help me with my problem, for starters here is a few commands that I ran just to make sure the drive is detected.
sudo fdisk -l
[sudo] password for tyon: 

Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x453a453a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3337    26804421   83  Linux
/dev/sda2           14245       14596     2827409+   5  Extended
/dev/sda3            3338       14244    87609344   83  Linux
/dev/sda5           14245       14596     2827408+  82  Linux swap / Solaris

Partition table entries are not in disk order

sudo lshw -c disk
  *-disk                  
       description: ATA Disk
       product: SAMSUNG SV1203N
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: TQ10
       serial: S01CJ10X920261
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=453a453a
  *-cdrom:0
       description: DVD-RAM writer
       product: DVD-RAM GSA-H55L
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.03
       serial: [HL-DT-STDVD-RAM GSA-H55L1.0307/08/17 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM DDU1615
       vendor: SONY
       physical id: 0.1.0
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/cdrom
       version: FDS1
       capabilities: removable audio dvd
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted

wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'     rwrw-- : 'HL-DT-ST' 'DVD-RAM GSA-H55L'

Thank you for your time and patience. Also does anyone know of a good video editor for linux, for my needs kinodv looks pretty nice but if anyone has other suggestions it would be greatly appreciated.

When I try to run mplayer in the terminal this is what I get:
mplayer /media/CDROM
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/CDROM.
Seek failed

---

### Post by DarinB on 2010-06-18
darin@darin-desktop ~ $ sudo lshw -c disk
  *-cdrom:0               
       description: CD-R/CD-RW writer
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw
       configuration: status=open
  *-cdrom:1
       description: DVD-RAM writer
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open
  *-cdrom:2
       description: DVD reader
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd2
       logical name: /dev/sr2
       capabilities: audio dvd
       configuration: status=open
  *-disk:0
       description: ATA Disk
       product: SAMSUNG HD753LJ
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 1AA0
       serial: S1D0J1CQB00750
       size: 698GiB (750GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=11446ceb
  *-disk:1
       description: ATA Disk
       product: SAMSUNG HD753LJ
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 1AA0
       serial: S1D0J1NQB00196
       size: 698GiB (750GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=790b971b
  *-disk
       description: ATA Disk
       product: ST3750640AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: 3.AA
       serial: 5QD15MNV
       size: 698GiB (750GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=790b9718
  *-disk:0
       description: SCSI Disk
       product: STORAGE DEVICE-A
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdd
       version: 9727
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:1
       description: SCSI Disk
       product: STORAGE DEVICE-A
       vendor: Generic
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sde
       version: 9727
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde
  *-disk:2
       description: SCSI Disk
       product: STORAGE DEVICE-A
       vendor: Generic
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdf
       version: 9727
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdf
  *-disk:3
       description: SCSI Disk
       product: STORAGE DEVICE-A
       vendor: Generic
       physical id: 0.0.3
       bus info: scsi@6:0.0.3
       logical name: /dev/sdg
       version: 9727
       serial: =
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdg
  *-disk:4
       description: SCSI Disk
       product: STORAGE DEVICE-A
       vendor: Generic
       physical id: 0.0.4
       bus info: scsi@6:0.0.4
       logical name: /dev/sdh
       version: 9727
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdh
  *-disk
       description: SCSI Disk
       product: Photosmart 2575
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdi
       version: 1.00
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdi
darin@darin-desktop ~ $ *-disk

---

