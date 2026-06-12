---
title: "GnomeBaker burn 48X CD-R error. HELP!"
date: 2006-03-28
forum: General Help
---

### Post by Neobuntu on 2006-03-28
Using GnomeBaker I went to burn another Ubuntu install CD from image. I put a 48X Kypermedia CD in and choose 48X and burn free but got theses errors. 

What's going on? What do I do now?

The CD seems to read OK now but I can't trust it because of these errors and the reported fail. Can someone put this into english for me please?

The following is the output in it's ...(now shortend % readout to fit forum)
---------------------------------------

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-10-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX215E5 '
Revision       : '6.1M'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P RAW/R16 RAW/R96R
Drive buf size : 1575840 = 1538 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data   617 MB         padsize:   30 KB
Total size:      709 MB (70:15.62) = 316172 sectors
Lout start:      709 MB (70:17/47) = 316172 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 43674
Starting to write CD/DVD at speed 40 in real TAO mode for multi session.
Last chance to quit, starting real write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Starting new track at sector: 0

Track 01:    0 of  617 MB written.
Track 01:    1 of  617 MB written (fifo  98%) [buf  95%]   5.9x.

(********SNIP********)

Track 01:  526 of  617 MB written (fifo  93%) [buf  84%]   9.1x.
Track 01:  527 of  617 MB written (fifo  95%) [buf  70%]   2.0x.
Track 01:  528 of  617 MB written (fifo  96%) [buf  61%]   2.1x.
Track 01:  529 of  617 MB written (fifo  92%) [buf  52%]   2.1x.
Track 01:  530 of  617 MB written (fifo  95%) [buf  38%]   1.2x.
Track 01:  531 of  617 MB written (fifo  93%) [buf  71%]   2.0x.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 04 26 B8 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 8.965s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 557170688 bytes
Writing  time:  721.813s
Average write speed   5.9x.
Min drive buffer fill was 10%
Fixating...
Fixating time:   27.642s
cdrecord: fifo had 8840 puts and 8777 gets.
cdrecord: fifo was 0 times empty and 5481 times full, min fill was 81%.

---

### Post by John.Michael.Kane on 2006-03-28
Neobuntu khyper media is not best media. so it could be that it was a bad disk. if you can reburn the iso using 40x speed to see if you get the same errors.

---

### Post by Neobuntu on 2006-03-28
Thanks Snake! 

The rep in MicroCenter (Georgia) told me they worked great for him. Man I hate the complexities of CD/DVD burning. I took back my DVD burner and I'm stopping here. No more matching media and having to burn a slow speeds to get a good copy. 

Anyway, so I went back to CD-RW drive to keep it simple and bought these KHypermedia CD's knowing they were 48X and figuring they would be a good match for my burner. I have burned CD-RW's with it fine and and wanted to move back to burn once CD's at 48X.

I note the readout got no where near 48X.  

What up with... 
"Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?". 
Is there some permission setting?

Is this bad?
"Manufacturer: CMC Magnetics Corporation"

I can certainly try another at 40X but I don't know why a 48X CD could do better at 40X. 

What low cost CD's ARE recomended?

What ever happend to keeping things simple.

I must say that Ubuntu and GnomeBaker are simple and better than that other OS but I don't know if there's a bug in GonmeBaker that you may know about. I am upgraded to the newest Breezy.

If you (all) can add anything and shed any light on this situation, I thank you.

---

### Post by taygan on 2006-06-20
make sure your dma is enabled..  My write speeds were slow until I enabled the direct access to the drive that dma allows.

Here's the hdparm for my drive (found at hdd, yours may be hdc or something similar)  Note that using_dma is on.

user@localhost:~$ hdparm /dev/hdd

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

---

