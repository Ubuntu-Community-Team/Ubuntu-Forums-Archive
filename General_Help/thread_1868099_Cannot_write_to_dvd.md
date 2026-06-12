---
title: "Cannot write to dvd"
date: 2011-10-23
forum: General Help
---

### Post by nnn= on 2011-10-23
I'm trying to write an iso of a cd to a dvd, but I'm getting errors when using brasero and wodim. For a filled dvd- the former says "an error has occurred" after a few seconds pass and the disc is ejected (when trying to blank as part of writing iso). The latter says this when trying to blank dvd-:
```
$ wodim -vv dev=/dev/sr0 blank=all
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
WARNING: /dev/sr0 seems to be mounted!
wodim: Device or resource busy.
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```
and this when writing to a blank dvd+ ```
$ wodim dev=/dev/sr0 -v -data 10.iso
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'SONY    '
Identification : 'DVD RW DW-U12A  '
Revision       : '2.0a'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001A (DVD+RW)
Profile: 0x001B (DVD+R)
Profile: 0x001A (DVD+RW) (current)
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
Drive buf size : 4194304 = 4096 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 18863 kB/s 107x CD 13x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data   684 MB        
Total size:      786 MB (77:52.85) = 350464 sectors
Lout start:      786 MB (77:54/64) = 350464 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
wodim: WARNING: Data may not fit on standard 74min disk.
Speed set to 3324 KB/s
Starting to write CD/DVD at speed   2.0 in real unknown mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 12 00 00 00 00 30 05 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.012s timeout 60s
wodim: OPC failed.
Writing  time:    0.098s
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

```How do I fix this? The cd/dvd writer I think supports writing only on dvd+, but I tried writing both dvd- and dvd+ and neither works. It reads, however, fine.

---

### Post by Bobhuber on 2011-10-23
Brasero has had problems for a long time with blanking or even using blank RW. Not familiar with Wodim. However you should be using a DVD R (not +RW) for iso files or you most likely will continue to have problems. If all else fails try loading K3B which is Multi Platform and works much better. Be aware that that will load a bunch of additional lib files that you will probably never use and I think are associated with KDE.

---

