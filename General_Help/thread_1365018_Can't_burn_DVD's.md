---
title: "Can't burn DVD's"
date: 2009-12-26
forum: General Help
---

### Post by SVEN1 on 2009-12-26
in Ubuntu 8.10 with any of the Burners supplied in the repros.
My DVD drives will burn any format if I can get a burner to work.
They all error.

Managed to get K3B to burn two jpg. pictures once!

The DVD's I am using are Verbatim DVD-R 4.7 GB 16x.

Any suggestions?

FRom Debugging screen:
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-16-generic
Devices
-----------------------
TOSHIBA DVD-ROM SD-R5112 1031 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R96R, Restricted Overwrite]

SONY DVD RW AW-Q170A 1.73 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump]
Burned media
-----------------------
DVD-R Sequential

K3bIsoImager
-----------------------
mkisofs print size result: 11770 (24104960 bytes)
Pipe throughput: 24104960 bytes read, 24104960 bytes written.

Used versions
-----------------------
mkisofs: 1.1.8
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd1 obs=32k seek=0'
/dev/scd1: "Current Write Speed" is 18.4x1352KBps.
:-[ WRITE@LBA=30h failed with SK=4h/LOGICAL UNIT COMMUNICATION CRC ERROR (ULTRA-DMA/32)]: Input/output error
:-( write failed: Input/output error
/dev/scd1: flushing cache
/dev/scd1: updating RMA
/dev/scd1: closing session

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd1=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:11770 -speed=18 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
11770
I: -input-charset not specified, using utf-8 (detected in locale settings)
  4.37% done, estimate finish Sat Dec 26 17:37:34 2009
  8.56% done, estimate finish Sat Dec 26 17:37:34 2009
 12.78% done, estimate finish Sat Dec 26 17:37:34 2009
 16.99% done, estimate finish Sat Dec 26 17:37:34 2009
 21.27% done, estimate finish Sat Dec 26 17:37:34 2009
 25.62% done, estimate finish Sat Dec 26 17:37:34 2009
 29.83% done, estimate finish Sat Dec 26 17:37:34 2009
 34.04% done, estimate finish Sat Dec 26 17:37:34 2009
 38.26% done, estimate finish Sat Dec 26 17:37:34 2009
 42.52% done, estimate finish Sat Dec 26 17:37:34 2009
 46.74% done, estimate finish Sat Dec 26 17:37:34 2009
 50.99% done, estimate finish Sat Dec 26 17:37:34 2009
 55.34% done, estimate finish Sat Dec 26 17:37:34 2009
 59.55% done, estimate finish Sat Dec 26 17:37:34 2009
 63.76% done, estimate finish Sat Dec 26 17:37:34 2009
 67.98% done, estimate finish Sat Dec 26 17:37:34 2009
 72.33% done, estimate finish Sat Dec 26 17:37:34 2009
 76.54% done, estimate finish Sat Dec 26 17:37:34 2009
 80.76% done, estimate finish Sat Dec 26 17:37:34 2009
 84.97% done, estimate finish Sat Dec 26 17:37:34 2009
 89.32% done, estimate finish Sat Dec 26 17:37:34 2009
 93.53% done, estimate finish Sat Dec 26 17:37:34 2009
 97.75% done, estimate finish Sat Dec 26 17:37:34 2009
Total translation table size: 0
Total rockridge attributes bytes: 1022
Total directory bytes: 1584
Path table size(bytes): 10
Max brk space used 0
11770 extents written (22 MB)

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Better Twice -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-sven/k3b46gXvb.tmp -rational-rock -hide-list /tmp/kde-sven/k3bmw9Foc.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-sven/k3bd3Uczb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-sven/k3bLa4Dqc.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Better Twice -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-sven/k3boiwmJb.tmp -rational-rock -hide-list /tmp/kde-sven/k3bLNAG6b.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-sven/k3b258Dzb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-sven/k3bUIDScb.tmp

---

### Post by dcstar on 2009-12-27
> **SVEN1 said:**
> in Ubuntu 8.10 with any of the Burners supplied in the repros.
My DVD drives will burn any format if I can get a burner to work.
They all error.
..........
growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd1 obs=32k seek=0'
/dev/scd1: "Current Write Speed" is 18.4x1352KBps.
:-[ WRITE@LBA=30h failed with SK=4h/LOGICAL UNIT **COMMUNICATION CRC ERROR (ULTRA-DMA/32)**]: Input/output error
:-( write failed: Input/output error
........

Manually check (and set) the Master/Slave settings on the drives, set the BIOS to the correct IDE cable type.

---

### Post by khelben1979 on 2009-12-27
Try to lower the burning speed at minimum to see if it makes any difference.

---

