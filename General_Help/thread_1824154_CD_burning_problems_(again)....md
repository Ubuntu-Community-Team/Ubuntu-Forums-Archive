---
title: "CD burning problems (again)..."
date: 2011-08-13
forum: General Help
---

### Post by t0p on 2011-08-13
I was having problems burning data to CD-Rs, and [TeoBigusGeekus graciously told me]("http://ubuntuforums.org/showthread.php?t=1822343") how to do it on the command line.  It worked yesterday.  But now it doesn't work, seemingly because of OPC failure (whatever that is).

Here's the output I get when I run the command:

```

t0p@phobos:~$ wodim -v dev=/dev/cdrom /home/t0p/May.iso
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : '_NEC    '
Identification : 'CDRW/DVD CB1100B'
Revision       : 'NS00'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Profile: 0x0010 (DVD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1278464 = 1248 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data   245 MB        
Total size:      281 MB (27:55.81) = 125686 sectors
Lout start:      282 MB (27:57/61) = 125686 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -12369 (97:17/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 234163
Speed set to 9173 KB/s
Starting to write CD/DVD at speed  52.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (valid) 
cmd finished after 28.251s timeout 60s
wodim: OPC failed.
Writing  time:   28.275s
BURN-Free was never needed.
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
t0p@phobos:~$ 

```

Is this a hardware problem (the computer is certainly no spring chicken!) or is it a software problem that can be fixed?  When I try to use K3b to burn a disk I also get an "OPC Failure" error.

Any ideas?  Cheers.

---

### Post by t0p on 2011-09-20
I've dug this one up again because I really would like some feedback on the problem.  I'm trying to burn an image to a CD-R using wodim as TeoBigusGeekus suggested [here]("http://ubuntuforums.org/showthread.php?t=1822343").  I ave found that it works for me [i]occasionally/i], if I try over and over; but it usually fails when trying to perform OPC.  Here's the outputting I'm getting:

```

t0p@phobos:~$ wodim -v dev=/dev/cdrw /media/8d514161-eaf5-4112-a721-dcd9d21e80a5/disk-images/pmagic-6.6.iso
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : '_NEC    '
Identification : 'CDRW/DVD CB1100B'
Revision       : 'NS00'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Profile: 0x0010 (DVD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1278464 = 1248 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data   172 MB        
Total size:      197 MB (19:34.21) = 88066 sectors
Lout start:      197 MB (19:36/16) = 88066 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -12369 (97:17/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 271783
Speed set to 9173 KB/s
Starting to write CD/DVD at speed  52.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (valid) 
cmd finished after 22.204s timeout 60s
wodim: OPC failed.
Writing  time:   22.229s
BURN-Free was never needed.
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
t0p@phobos:~$ 

```

Anyone got any idea why this is happening?  What can I do to improve success rate?  Cheers.

---

### Post by TeoBigusGeekus on 2011-10-02
Try reducing the burn speed:
```
wodim -v dev=/dev/cdrw speed=4 /media/8d514161-eaf5-4112-a721-dcd9d21e80a5/disk-images/pmagic-6.6.iso
```
If that fails, try with speed=2 or speed=0 (use lowest possible speed on this device).

---

