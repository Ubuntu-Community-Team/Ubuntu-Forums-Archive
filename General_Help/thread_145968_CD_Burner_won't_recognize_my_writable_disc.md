---
title: "CD Burner won't recognize my writable disc"
date: 2006-03-17
forum: General Help
---

### Post by TheBlackNoodle on 2006-03-17
So I just installed Ubuntu on an older computer, and I'm testing everything out. Seems like the CD Burner is giving me problems.

I copy and paste some files to the CD-ROM Drive. I go into the drive, right-click the background, and hit Write To Disc. The Write To Disc dialog pops up, and all the information seems correct. I hit Write. I get the following error in a new dialog box.

"Insert a rewritable or blank disc.
Please put a CD-R/CD-RW, with at least X MiB free into the drive."

I say X because I tried burning files sized between 20 K and 530 MB. Same error either way. I just nuked Windows from this computer and I know the CD burner worked there (although only with Easy CD Creator 4), so I'm pretty sure it's not a hardware issue. The CD drive is a HP CD-Writer Plus.

The burner works on my laptop. I tested the CD's--they work, as well. Any ideas what's going on here?

---

### Post by andreytcho on 2006-03-17
why aren't you using K3B ? it is like easy cd-creator/nero and it will give you some idea what works and what doesn't with an appropriate message.

---

### Post by TheBlackNoodle on 2006-03-17
Okay, installed K3B and tried it out. I still get pretty much the same error.

I set up my files in K3B, go into the Burn dialog and (after checking out the defaults) hit Burn. A new dialog box pops up:

Waiting for Disk - K3b
Found media: CD-R (appendal
Please insert an empty CD-R(W) medium into drive
TEAC CDW54E (/dev/hdc)

I tried forcing a burn just to get some debug output. Here's the output:

```
System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
TEAC CD-W54E 1.1C (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; SAO/R96P; SAO/R96R]

K3b
-----------------------
Size of filesystem calculated: 186

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
cdrecord: 2.1.1a01

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
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'TEAC    '
Identifikation : 'CD-W54E         '
Revision       : '1.1C'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R
Drive buf size : 1300480 = 1270 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data     0 MB         padsize:  228 KB
Total size:        0 MB (00:04.00) = 300 sectors
Lout start:        1 MB (00:06/00) = 300 sectors
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
Blocks total: 359846 Blocks current: 231357 Blocks remaining: 231057
Starting to write CD/DVD at speed 4 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 01 F6 7F 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.000s timeout 200s
Writing pregap for track 1 at 128639
write track pad data: error after 0 bytes
BFree: 1458 K BSize: 1458 K
Starting new track at sector: 128789
Track 01:    0 of    0 MB written.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 01 F7 15 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.000s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:    8.353s
Average write speed   0.8x.
Fixating...
Fixating time:    0.008s
/usr/bin/X11/cdrecord: fifo had 6 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=4 -dao -eject -data -tsize=186s - 

mkisofs
-----------------------
186
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
Total translation table size: 0
Total rockridge attributes bytes: 337
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 21000
186 extents written (0 MB)

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-helene/k3bwOusJa.tmp -rational-rock -hide-list /tmp/kde-helene/k3b7y1Eeb.tmp -joliet -hide-joliet-list /tmp/kde-helene/k3bFWBbJa.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-helene/k3bKiW4tb.tmp 
```

It gives an error saying there isn't enough space on the disk. But I know there is. I'm trying to burn a 10kb file.

---

### Post by TheBlackNoodle on 2006-03-17
Tried some more things, tried looking up more solutions in google. Can't find much.

```
root@ubuntu:/home/user# mount -t iso9660 /dev/hdc /mnt/cdrom
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I get the same error with mount /dev/hdc and mount /dev/hdc /media/cdrom0. My fstab settings are identical to the ones on my laptop. No idea why this is going on...

EDIT:
Also should mention that the icon on GNOME desktop appears as CD-ROM rather than CD-R or CD-RW like it does on my laptop.

---

### Post by Scottydogg on 2008-02-07
Exact same problem for me.  I can't mount  audio discs (but listen with some programs).  No big deal.  But regardless of what program I use, it always tells me to insert a blank disc. :mad: I have inserted a blank disc!!
can anyone help?:confused:

---

### Post by yaitedog on 2008-02-29
I'm using a sony burner and have the same issue. I found some data here [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/8987](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/8987) 
Its over my head though

---

### Post by Scottydogg on 2008-03-01
For me the fix turned out to be installing gnomebaker.  For reasons unknown, my hardware works  with that program but none of the others I tried.  Thank you, oh makers of GnomeBaker!

---

### Post by yaitedog on 2008-03-02
Alrighty then I'll try it. Thanks Scottydog. anybody with more Linux knowledge check out bug 8987 I linked to above?

---

### Post by Pygi on 2008-03-03
> **Scottydogg said:**
> For me the fix turned out to be installing gnomebaker.  For reasons unknown, my hardware works  with that program but none of the others I tried.  Thank you, oh makers of GnomeBaker!

Haha, interesting. And I was thinking of replacing the devices detection code for next Gnomebaker. Would you be willing to test it once it's ready? :)

KR.

---

### Post by Scottydogg on 2008-03-03
> **Pygi said:**
> Haha, interesting. And I was thinking of replacing the devices detection code for next Gnomebaker. Would you be willing to test it once it's ready? :)

KR.

Pygi,
I'd be  happy to test it out.  
*warning* you'll have to walk me through it, I'm a  biologist, not a computer programer.  That said, I love Ubuntu/Linux and am glad to contribute  any way I can.

---

