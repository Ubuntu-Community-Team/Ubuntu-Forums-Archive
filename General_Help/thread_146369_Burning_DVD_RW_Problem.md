---
title: "Burning DVD RW Problem"
date: 2006-03-18
forum: General Help
---

### Post by GreveFelix on 2006-03-18
Hi everybody,
I am using the Ubuntu cd/DVD burning tool, and i did not find a possibility to formate a rewritable  DVD -  to earase the Data on it. So I whould be able to burn new files on it.
Should I use another programm? And if ... which?  



And by the way another question: I am able to burn CD but as I tried to burn some Musik files, Ubuntu told me: "some files have invalid names". Why ? What kind of Symbol is not allowed in a Name?

Thanks for help .... ;)

---

### Post by taurus on 2006-03-18
And what is the name of that tool?  I think you should use k3b and there is an option where you can have k3b to automatically erase your CD-RW/DVD-RW before it copies new data to it.  And regarding your second question, I bet it has something to do with empty space between words!!!

---

### Post by BoyOfDestiny on 2006-03-18
[QUOTE=GreveFelix]Hi everybody,
I am using the Ubuntu cd/DVD burning tool, and i did not find a possibility to formate a rewritable  DVD -  to earase the Data on it. So I whould be able to burn new files on it.
Should I use another programm? And if ... which?  



And by the way another question: I am able to burn CD but as I tried to burn some Musik files, Ubuntu told me: "some files have invalid names". Why ? What kind of Symbol is not allowed in a Name?

Thanks for help .... ;)[/QUOTE]

Just try and burn the disc, it will prompt you that it's not empty, would you like to erase it... As for the filename thing, same issue for me...Dunno.

---

### Post by GreveFelix on 2006-03-18
Hi, 
thanks for your help, the k3b looks good. But it seems like I have no DVD RW Support. Because as I tried to erase a RW DVD. The Programm tould me, I should  insert a RW DVD in (but it already was a RW DVD). As I asked the PRogramm to give me more Details it tould me:

.........
/usr/bin/X11/cdrecord: Found DVD+ media but DVD+R/DVD+RW support code is missing.
/usr/bin/X11/cdrecord: If you need DVD+R/DVD+RW support, ask the Author for cdrecord-ProDVD.
/usr/bin/X11/cdrecord: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
..............

And thats maybe why it also did not work, with the Ubuntu tool! 

Any idears how to instal this DVD RW support and why it is not already integrated in the Burning Programms?
Thanks for help 




The whole Text the programm tould me:
System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4120B A100 (/dev/hdc, ) at /media/cdrom1 [CD-R; CD-RW; CD-Rom; DVD-Rom; DVD-Ram; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R doppelschichtig] [DVD-Rom; DVD-R Sequentiell; DVD-Ram; DVD-RW Eingeschränktes Überbrennen; DVD-RW Sequentiell; DVD+RW; DVD+R; DVD+R Doppelschicht; CD-Rom; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Eingeschränktes Überschreiben]

HL-DT-ST DVD-ROM GDR8161B 0100 (/dev/hdd, ) at /media/cdrom0 [CD-Rom; DVD-Rom] [DVD-Rom; CD-Rom] [Keine]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=31 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-10-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: Found DVD+ media but DVD+R/DVD+RW support code is missing.
/usr/bin/X11/cdrecord: If you need DVD+R/DVD+RW support, ask the Author for cdrecord-ProDVD.
/usr/bin/X11/cdrecord: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4120B'
Revision       : 'A100'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001A
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A (current)
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-ROM driver (mmc_cd).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 851968 = 832 KB
Drive DMA Speed: 1043 kB/s 5x CD 0x DVD
Current Secsize: 2048
Waiting for drive to calm down.
Starting to write CD/DVD at speed 18 in real force BLANK mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 A1 00 00 0F 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 9600s
Starting to write CD/DVD at speed 18 in real force BLANK mode for single session.
No chance to quit anymore. Operation starts.
/usr/bin/X11/cdrecord: Cannot blank disk, aborting.
/usr/bin/X11/cdrecord: Some drives do not support all blank types.
/usr/bin/X11/cdrecord: Try again with cdrecord blank=all.
This drive or media does not support the 'BLANK media' command

---

### Post by taurus on 2006-03-18
Sometimes k3b (or Ubuntu) has problem reading some cheap DVD media so what brand name do you use right now?  Do you have another brand that you can test out?

---

### Post by GreveFelix on 2006-03-19
Yes, it a cheap one out of a supermarket. Which one should I use ?

---

### Post by taurus on 2006-03-19
So far, I have great success with Verbatim, Memorex, and TDK (cheapest of three)...

---

### Post by GreveFelix on 2006-03-19
I will try them ....

Thanks for your help .... 

:p

---

### Post by linuxismywife on 2006-08-29
any help on solving the dvd rw erasing problem? 

i also faced the same problem

---

