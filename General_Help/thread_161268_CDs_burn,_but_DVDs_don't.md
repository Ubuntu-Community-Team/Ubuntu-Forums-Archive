---
title: "CDs burn, but DVDs don't?"
date: 2006-04-16
forum: General Help
---

### Post by rainbowjoshua on 2006-04-16
They both used to, and now I just got my motherboard RMA back and I can burn CDs, but not DVDs.  My k3b log is:

```

System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.5.1
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
LITE-ON DVDRW SOHW-1673S JS01 (/dev/hdd, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

K3b
-----------------------
Size of filesystem calculated: 2153118

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
growisofs: 5.21

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdd obs=32k seek=0'
/dev/hdd: "Current Write Speed" is 6.1x1385KBps.
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
         0/4409585664 ( 0.0%) @0x, remaining ??:??
:-( unable to WRITE@LBA=0h: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdd=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2153118 -dvd-compat -speed=2 

mkisofs
-----------------------
2153118
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid movies -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-joshua/k3bQjz11a.tmp -rational-rock -hide-list /tmp/kde-joshua/k3bkAuz3b.tmp -joliet -hide-joliet-list /tmp/kde-joshua/k3bJIrHTb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-joshua/k3bK2lAcc.tmp 


```

Anyone had similar problems?
Joshua

---

