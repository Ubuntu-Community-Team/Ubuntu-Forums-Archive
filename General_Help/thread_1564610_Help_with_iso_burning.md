---
title: "Help with iso burning"
date: 2010-08-30
forum: General Help
---

### Post by Zirts on 2010-08-30
Hi,

I'v been trying to get my windows .iso on a cd for a long time allrdy now, as I need it for the latest Photoshop...

I'v bought like 7 different DVD's and none work, i have even downloaded different .iso 's and still no luck...

Latest error report is this:
```

Devices
-----------------------
TSSTcorp CD/DVDW SH-W162C TS06 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.2 (KDE 4.4.2)
QT Version:  4.6.2
Kernel:      2.6.32-24-generic

Used versions
-----------------------
cdrecord: 1.1.10

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CD/DVDW SH-W162C'
Revision       : 'TS06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x002B (DVD+R/DL)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x002B (DVD+R/DL) (current)
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1048576 = 1024 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 2770 KB/s
Track 01: data   691 MB        
Total size:      793 MB (78:38.06) = 353855 sectors
Lout start:      794 MB (78:40/05) = 353855 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 4173824 Blocks current: 4173824 Blocks remaining: 3819969
Starting to write CD/DVD at speed   2.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
dvd_dual_layer_split: read_dvd_structure returns invalid data
Preparing middle zone location for this DVD+R dual layer disc
Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 05 66 3F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 19.114s timeout 200s
/usr/bin/wodim: Cannot open new session.
input buffer ready.
Writing  time:   19.144s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=2 -sao driveropts=burnfree -data -tsize=353855s -


```

Also worth to mention i'v tryied about 4 different burining programs.
It can't be the fault of the CD-ROM too as it worked before I got Ubuntu on it.

Maybe it's some frimware fault or something? I did install some DVD and CD burining lib packages but they were no help, also I can see that the CD-ROM is labelled as Writemaster, so I guess that's the name of the company that made it?

---

### Post by lombaardcj on 2010-09-06
So you probably tried Brasero and others to write?

I've never had a problem writing ISO's to disk. 

I'm using Brasero 2.30.2 as we speak to burn the latest Ubuntu Server Image to disk for test drive on my laptop.

Choose "Burn Image" from main option list, Select the iso file and Burn away.

You say the disk don't work.  Have you considered that the iso might be at fault for your problem?

---

