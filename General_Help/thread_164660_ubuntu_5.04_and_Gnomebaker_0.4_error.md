---
title: "ubuntu 5.04 and Gnomebaker 0.4 error"
date: 2006-04-23
forum: General Help
---

### Post by TitusDalwards on 2006-04-23
when i try to cd record with gnomebaker 0.4 i got these error messages:

> cdrecord: Warning: Running on Linux-2.6.10-5-686-smp
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
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1
'@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type : Removable CD-ROM
Version : 0
Response Format: 1
Vendor_info : 'CENDYNE_'
Identifikation : '481648AX '
Revision : '150F'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
resid: 64508
resid: 64508
resid: 64512
cdrecord: Success. read buffer: scsi sendcmd: no error
CDB: 3C 00 00 00 00 00 00 FC 00 00
status: 0xb (Reserved)
Sense Bytes:
Sense Key: 0xFFFFFFFF [], Segment 0
Sense Code: 0x00 Qual 0x00 (no additional sense information) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 64512
cmd finished after 85.171s timeout 40s

but when i change GnomeBaker 0.4.4 to GnomeBaker 0.3.3 everything seems well.

(my kernel version is 2.6.10)

have you ever heard any problem like mine?

---

