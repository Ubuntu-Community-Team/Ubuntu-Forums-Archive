---
title: "ripping psx games"
date: 2010-08-09
forum: General Help
---

### Post by proevofanatik on 2010-08-09
i am trying to rip my psx game to an image file so that i can convert it to play on my psp. i have installed Gtk Popstation and that seems to be working no problem. but i read on another forum that to rip my psx game i need to go to terminal and do the following.

cdrdao read-cd --read-raw --datafile isspro.bin \
--device /dev/sr0 --driver generic-mmc-raw isspro.toc

when i do that, this comes up.

$ cdrdao read-cd --read-raw --datafile isspro.bin \
> --device /dev/sr0 --driver generic-mmc-raw isspro.toc
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
ERROR: Cannot open SCSI device '/dev/sr0': Cannot open '/dev/sr0'
Supported SCSI transports for this platform:

Transport name:         sg
Transport descr.:       Generic transport independent SCSI
Transp. layer ind.:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         pg
Transport descr.:       SCSI transport for ATAPI over Parallel Port
Transp. layer ind.:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         ATA
Transport descr.:       ATA Packet specific SCSI transport
Transp. layer ind.:     ATAPI:
Target specifier:       bus,target,lun
Target example:         ATAPI:1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         ATA
Transport descr.:       ATA Packet specific SCSI transport using sg interface
Transp. layer ind.:     ATA:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported
ERROR: Please use option '--device [proto:]bus,id,lun', e.g. --device 0,6,0 or --device ATA:0,0,0
ERROR: Cannot setup device /dev/sr0.


what am i doing wrong?

---

### Post by proevofanatik on 2010-08-09
any ideas anyone?

---

### Post by proevofanatik on 2010-08-10
im sorry to keep bumping this thread but can anyone please tell me where im going wrong?

---

