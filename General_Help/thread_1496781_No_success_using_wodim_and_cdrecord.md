---
title: "No success using wodim and cdrecord"
date: 2010-05-29
forum: General Help
---

### Post by HotForLinux on 2010-05-29
For the first time, I tried to use the command line to burn an iso image onto a cd. 
According to the instructions, which I read in many places, I should use the following command:
> **cdrecord -v -dao dev=1,0,0  ./live-cd.iso**
or
** wodim -v -dao dev=1,0,0  ./live-cd.iso**

Once *cdrecord -scanbus* told me the device was at 1,0,0

But, since this command flooded the screen with the following error message,

> 
*".Unable to open this SCSI ID. Trying to map to old ATA syntax.This workaround will disappear in the near future. Fix your configuration.Unable to open this SCSI ID. Trying to map to old ATA syntax.This workaround will disappear in the near future. Fix your configuration.Unable....."*I tried the following (in an Ubuntu-Hardy desktop):

```
**$ wodim -v -dao dev=/dev/scd0  ./live-cd.iso**
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-RAM UJ-830S '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A (CD-RW)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data   674 MB        
Total size:      774 MB (76:43.49) = 345262 sectors
Lout start:      774 MB (76:45/37) = 345262 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 2
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -12900 (97:10/00)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  4 1T speed high: 10
  2T speed low:  4 2T speed high:  0 (reserved val  6)
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 26 B2 48
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
Manufacturer is unknown because of the orange forum embargo.
As the orange forum likes to get money for recent information,
it may be that this media does not use illegal manufacturer coding.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 14587
Speed set to 1764 KB/s
Starting to write CD/DVD at speed  10.0 in real SAO mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:  674 of  674 MB written (fifo 100%) [buf  97%]  10.4x.
Track 01: Total bytes read/written: 707096576/707096576 (345262 sectors).
Writing  time:  485.089s
Average write speed   9.6x.
Min drive buffer fill was 97%
Fixating...
Fixating time:   13.656s
BURN-Free was never needed.
wodim: fifo had 11138 puts and 11138 gets.
wodim: fifo was 0 times empty and 10939 times full, min fill was 98%.
```Which seemes to have written nothing to the cd. So:
1) where was all that written?
2) how to use the command line to write CDs?

---

### Post by schily on 2010-05-31
Your main problem is that you don't use cdrecord but a defective fork.

The problems you describe do not exist in the original software
and did never exist in the original software.

See:

[ftp://ftp.berlios.de/pub/cdrecord/alpha/](ftp://ftp.berlios.de/pub/cdrecord/alpha/)

[http://cdrecord.berlios.de/](http://cdrecord.berlios.de/)

---

### Post by HotForLinux on 2011-06-04
WoW!

So  whats the version that we should install for Ubunu?
The cdrtools-3.01a04.tar.gz?

---

### Post by joubertdj on 2011-07-28
Try this: [http://forum.ubuntuusers.de/topic/kleines-projekt-mit-paketverwaltung-die-schil/8/#post-2809761](http://forum.ubuntuusers.de/topic/kleines-projekt-mit-paketverwaltung-die-schil/8/#post-2809761)

It works perfectly ...

You would think that Ubuntu testers/maintainers could figure it out ?

---

