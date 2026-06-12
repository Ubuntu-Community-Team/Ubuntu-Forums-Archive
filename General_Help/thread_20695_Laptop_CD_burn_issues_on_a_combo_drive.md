---
title: "Laptop CD burn issues on a combo drive"
date: 2005-03-18
forum: General Help
---

### Post by uberlinux on 2005-03-18
so I've got this laptop and doing anything involving the DVD/CD-RW drive is very difficult, but I have finally got the symlink thingy to get DVD's to play on mplayer, but I would love to burn CD's now, and I havent gotten anything to work yet, so here goes...
___________________________________________________________________________________
```

System
-----------------------
K3b Version:0.11.18 
KDE Version: 3.2.3
QT Version: 3.2.3

cdrecord
-----------------------
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
/usr/bin/cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
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
Vendor_info    : 'ASUS    '
Identifikation : 'SCB-2424        '
Revision       : '1.00'
Device seems to be: Generic CD-ROM.
Using generic SCSI-2       CD-ROM driver (scsi2_cd).
Driver flags   : 
Supported modes: 
FIFO size      : 4194304 = 4096 KB
/usr/bin/cdrecord: Drive does not support TAO recording.
/usr/bin/cdrecord: Illegal write mode for this drive.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=24 -tao driveropts=burnfree -eject -data -tsize=182s - 

mkisofs
-----------------------
182
INFO: ISO-8859-1 character encoding detected by locale settings.
 Assuming ISO-8859-1 encoded filenames on source filesystem,
 use -input-charset to override.
Total translation table size: 0
Total rockridge attributes bytes: 251
Total directory bytes: 0
Path table size(bytes): 10
/usr/bin/mkisofs: Connection reset by peer. cannot fwrite 2048*1

mkisofs comand:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR VERSION 0.11.18 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer K3b - Version 0.11.18 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-default/k3bWon69b.tmp -rational-rock -hide-list /tmp/kde-default/k3b5vzTCa.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-default/k3bCfo6Sb.tmp /home/default/.kde/share/apps/k3b/temp/dummydir0/ 


```
______________________________________________________________________________________

I've got a 24x asus if that helps, I'm using warty with gnome.
I have tried this on k3b, gcombust, and even gnome-baker, all with the same results.
                                 Thanks in advance, Cody

---

