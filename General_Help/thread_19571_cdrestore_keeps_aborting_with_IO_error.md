---
title: "cdrestore keeps aborting with IO error"
date: 2005-03-12
forum: General Help
---

### Post by ryguasu on 2005-03-12
I'm wondering if you could help me diagnose my trouble
with cdbackup/cdrestore. I'm trying to do backups
with the following command:

cdbackup -d /dev/cdrom -r /dev/cdrom -s 4 -v -l 640 -m -a backup < backup.tar

and to do restores with:

cdrestore -v -d /dev/cdrom -l 640 -t 1 > restored.tar

I've been testing whether this backup solution actually works,
and so far it never does. Although cdbackup seems to
work without errors, I can never
manage a restore; cdrestore always ends up at some point
aborting with "Error reading data: Input/output error".
The error does not take place at a deterministic time; sometimes
it happens right after I initiate the cdrestore command,
while at other times the restore gets almost finished
before the abort. But it never manages to finish.

I'm pretty sure the problem is not with my CD-Rs; I've tried
about ten different ones, all with the same result.

I think the following information about my hardware and software
might be useful:

----------

Toshiba Satelite A-60

----------

Ubuntu Warty

root@cyan:/home # uname -a
Linux cyan 2.6.8.1-3-386 #1 Thu Nov 18 11:47:33 UTC 2004 i686 GNU/Linux

----------

cdbackup version: 0.6.3 (compiled Aug 14 2004)

cdrecord version: Cdrecord-Clone 2.01a29

----------

It's an ATAPI/ATA/whatever CD-R drive, with the following info:

root@cyan:~/restore-test # cdrecord dev=/dev/cdrom -scanbus
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'MATSHITA' 'UJDA760 DVD/CDRW' '1.50' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *

----------

when cdbackup calls cdrecord, the following gets printed:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

Using libscg version 'ubuntu-0.8ubuntu1'.
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'MATSHITA'
Identifikation : 'UJDA760 DVD/CDRW'
Revision       : '1.50'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Starting to write CD/DVD at speed 4 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Track 01: Total bytes read/written: 530755584/530755584 (259158 sectors).

---

