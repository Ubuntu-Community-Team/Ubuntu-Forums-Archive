---
title: "Can't burning CD/DVD"
date: 2006-06-21
forum: General Help
---

### Post by elcepi on 2006-06-21
I have been trying to burn an image with Ubuntu 6.06 and kernel 2.6 without any success.  When I try to burn it it complains that there is no disk on the drive.

I look and apparently you need to manually load the ide-cd module and then try to burn but it does not seem to help.

Here is the output of using cdrecord:
```
user@localhost:~/Desktop$ sudo cdrecord -v speed=1 dev=ATAPI:0,0,0 ubuntu-6.06-desktop-i386.iso
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-23-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: 'ATAPI:0,0,0'
devname: 'ATAPI'
scsibus: 0 target: 0 lun: 0
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'PHILIPS '
Identifikation : 'DVD+-RW DVD8801 '
Revision       : '2D06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0000
Profile: 0x002B
Profile: 0x001B
Profile: 0x001A
Profile: 0x0016
Profile: 0x0015
Profile: 0x0014
Profile: 0x0013
Profile: 0x0011
Profile: 0x0010
Profile: 0x000A
Profile: 0x0009
Profile: 0x0008
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
FIFO size      : 4194304 = 4096 KB
Track 01: data   697 MB
Total size:      801 MB (79:23.98) = 357299 sectors
Lout start:      801 MB (79:25/74) = 357299 sectors
cdrecord: Input/output error. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 12 00 00 00 00 3A 00 00 00 00 00 00 00 00 00 00 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.002s timeout 40s
cdrecord: No disk / Wrong disk!

```

And some info that I hope will be usefull:
```
user@localhost:~$ dmesg | grep hda
[4294667.296000] Kernel command line: root=/dev/sda1 ro quiet splash hda=ide-cd
[4294667.296000] ide_setup: hda=ide-cd
[4294671.584000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294671.950000] hda: PHILIPS DVD+/-RW DVD8801, ATAPI CD/DVD-ROM drive
[4294672.470000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)

```

```
user@localhost:~$ sudo cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-23-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.33
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'ATA     ' 'ST3160812AS     ' '3.AD' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *


```

```
user@localhost:~$ sudo cdrecord dev=ATA -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-23-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATA'
devname: 'ATA'
scsibus: -2 target: -2 lun: -2
Warning: Using badly designed ATAPI via /dev/hd* interface.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'PHILIPS ' 'DVD+-RW DVD8801 ' '2D06' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *


```

```
user@localhost:~$ uname -a
Linux localhost 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

```

---

### Post by anaconda on 2006-06-21
OK.. this may sound (and be) stupid question, but 
Why dont you install k3b and use it to burn your images? I mean it is really easy to use, and works realy well..

Sorry cant help you with command-line-burning

---

### Post by elcepi on 2006-06-21
I try it but I get the following error message:

```

Found media: **No media**

Please insert an empty CD-R(W) medium into drive

**Philios DVD+-RW DVD8801 (/dev/hda)**

```
I also tred with nautilus, but both use cdrecord to perform the low level operations.

---

