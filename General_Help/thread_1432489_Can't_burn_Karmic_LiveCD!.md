---
title: "Can't burn Karmic LiveCD!"
date: 2010-03-17
forum: General Help
---

### Post by squareff255 on 2010-03-17
I'm trying to burn a 9.10 LiveCD so I can install it on a friends computer. I'm just using the standard Ubuntu 9.10 desktop .iso image and I've burned many cd's with it in the past. I'm using the cdrecord command and it's giving the following output:
```

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
WARNING: the deprecated pseudo SCSI syntax found as device specification.
Support for that may cease in the future versions of wodim. For now,
the device will be mapped to a block device file where possible.
Run "wodim --devices" for details.
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RW GWA-4165B'
Revision       : 'DG01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 13963 kB/s 79x CD 10x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data   689 MB        
Total size:      792 MB (78:30.24) = 353268 sectors
Lout start:      792 MB (78:32/18) = 353268 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 6581
Speed set to 7056 KB/s
Starting to write CD/DVD at speed  40.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:  638 of  689 MB written (fifo 100%) [buf 100%]  16.3x.Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 04 FC B1 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 10 34 14 04 80 09 01 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x01 (tracking servo failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.010s timeout 40s

write track data: error after 669353984 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Writing  time:  176.378s
Average write speed  26.7x.
Min drive buffer fill was 86%
Fixating...
Fixating time:    0.004s
wodim: fifo had 10735 puts and 10544 gets.
wodim: fifo was 0 times empty and 6635 times full, min fill was 84%.

```
Can anyone translate...?  :-/ no idea...

---

### Post by Gadgetech on 2010-03-17
Well, I see some lines that say
```
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x01 (tracking servo failure) Fru 0x0
```

Sounds to me like your burner might have toasted itself. I've racked my brains in the past, burning multiple coasters until I finally realized I had a hardware problem.

---

### Post by DawieS on 2010-03-18
> **squareff255 said:**
> 
Starting to write CD/DVD at speed  40.0 in real TAO mode for single session.


Rather install Brasero disk burner, (or other preferred burner) where you have full control of the burning speed. Burn at a slower speed (for example x 16), and check the integrity of the CD/DVD.

I have wasted a lot of disks trying to burn at maximum speed.
:grin:

---

