---
title: "Can't burn ISO's in 11.10"
date: 2011-10-31
forum: General Help
---

### Post by adamklempner on 2011-10-31
I've recently upgraded to Ubuntu 11.10 from the software center, and now I am trying to burn ISO images and am encountering a problem that I did not have in 11.04.  I get this error using Brasero, and something similar with xfburn and k3b:

"SCSI error on write(96,16): [5 21 02] Invalid address"

Here is the session log output from Brasero, please help!:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_VDQO3V.bin toc = none
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_01PO3V.bin toc = none
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_PHQO3V.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/adam/Downloads/ubuntu-11.10-desktop-i386.iso (size = 729067520)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) c396dd0f97bd122691bdb92d7e68fde5 ((null) before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_tracks
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 0
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn cd Profile= 09h , obs= 32768 , obs_pad= 0
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn TAO pre-track 01 : get_nwa(0)=1, d=0 , demand=729067520 , cap=736960512

BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [5 21 02] Invalid address
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(96,16): [5 21 02] Invalid address
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 1
	message	= "SCSI error on write(96,16): [5 21 02] Invalid address"
BraseroLibburn stopping
Session error : SCSI error on write(96,16): [5 21 02] Invalid address (brasero_burn_record brasero-burn.c:2856)
```

---

### Post by Script Warlock on 2011-10-31
try to check another empty disk first.

---

### Post by vat with tux on 2011-10-31
Have you tried burning another ISO .... may be possible that it's problem with that ISO only...

---

### Post by PGScooter on 2011-10-31
can you burn things besides ISOs?

---

### Post by adamklempner on 2011-11-01
Thanks for the replies guys.  To answer the questions:

- I've tried several cd's, made a bunch of coasters
- I've tried other (known good) ISO's
- And I just attempted to write a Data CD with K3b, no luck.  Here is the output from that failure:


```
Devices
-----------------------
TSSTcorp CDDVDW SH-S223Q SB00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 61403 (125753344 bytes)

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.7.2 (4.7.2)
QT Version:  4.7.4
Kernel:      3.0.0-12-generic

Used versions
-----------------------
mkisofs: 1.1.11
cdrecord: 1.1.11

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.11
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDDVDW SH-S223Q '
Revision       : 'SB00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0017 (Reserved/Unknown) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1962752 = 1916 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 8468 KB/s
Track 01: data   119 MB        
Total size:      137 MB (13:38.73) = 61405 sectors
Lout start:      138 MB (13:40/55) = 61405 sectors
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
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 298441
Starting to write CD/DVD at speed  48.0 in real TAO mode for multi session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  119 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 1F 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.822s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 63488 bytes
Writing  time:   17.021s
Average write speed 139.0x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 03 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x03 (session fixation error - incomplete track in session) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 480s
=== last message repeated 2 times. ===
/usr/bin/wodim: Cannot fixate disk.
Fixating time:    0.004s
/usr/bin/wodim: fifo had 193 puts and 2 gets.
/usr/bin/wodim: fifo was 0 times empty and 1 times full, min fill was 99%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=48 -tao driveropts=burnfree -multi -xa -tsize=61403s -

mkisofs
-----------------------
61403
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.84% done, estimate finish Tue Nov  1 10:36:55 2011
  1.64% done, estimate finish Tue Nov  1 10:36:55 2011
  2.45% done, estimate finish Tue Nov  1 10:36:55 2011
  3.26% done, estimate finish Tue Nov  1 10:36:55 2011
  4.09% done, estimate finish Tue Nov  1 10:36:55 2011
  4.90% done, estimate finish Tue Nov  1 10:36:55 2011
  5.71% done, estimate finish Tue Nov  1 10:36:55 2011
  6.52% done, estimate finish Tue Nov  1 10:36:55 2011
  7.33% done, estimate finish Tue Nov  1 10:36:55 2011
  8.17% done, estimate finish Tue Nov  1 10:36:55 2011
  8.98% done, estimate finish Tue Nov  1 10:36:55 2011
  9.78% done, estimate finish Tue Nov  1 10:36:55 2011

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Offspring - Greatest Hits 2005 -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-adam/k3bb12402.tmp -rational-rock -hide-list /tmp/kde-adam/k3bc12402.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-adam/k3bh12402.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-adam/k3bF12402.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Offspring - Greatest Hits 2005 -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-adam/k3bm12402.tmp -rational-rock -hide-list /tmp/kde-adam/k3bt12402.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-adam/k3bn12402.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-adam/k3bQ12402.tmp

```

---

### Post by adamklempner on 2011-11-01
I should also mention that it reads CDs/DVDs fine.  Any idea's as to what I can check?

---

### Post by quasimodo69 on 2011-11-04
Hi Gang,
I am also having trouble burning a disc and in stalling the new 11.0 from an image.
tried 3 different image .iso sources.Keeps saying corrupted .iso or can not read image...

Using Brasero..never had this before.

Also...I am still a newbie.How do you use checksum?I mean step by step?Sorry but I have searched the net and am either retarded...or somebody is not explaining it simply enough.
Thnx Mucho

---

### Post by goashdag on 2011-11-04
im tryin to burn iso in k3b but getting error saying seems not to be useable image any1 help plz

---

### Post by interzoneuk on 2011-11-07
This has to be the absolute worst release ever - this is a pretty major bug !

Thankfully I use Arch Linux (kde) as my main OS so I have a usable desktop.

Bug report here

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/848340?comments=all](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/848340?comments=all)

---

### Post by WhiteSphinx on 2011-12-13
I am having the same problem with Brasero.  I am unable to write audio or video disks.  Data disks only.

---

### Post by ktec on 2011-12-23
Same problem here :(

I have to agree with [interzoneuk]("http://ubuntuforums.org/member.php?u=41367") here - not happy. Is it time for Mint?

---

### Post by xraynorm on 2012-01-08
Mint has the same problem.

---

### Post by adamklempner on 2012-02-12
Just an update, I put a different burner in the computer in case it was a hardware failure.  Burning any sort of disc still fails... :(  Perhaps the problem is that we are using a broken version of cdrtools due to bickering between its developers long ago:

[http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)

I tried the fix listed at the bottom, but no luck.  The error changed a little but was basically the same thing.

I've downloaded the trial version of Nero Linux 4 and will be using that for now.  It is good for 30 days.  I've just successfully completed my first CD burn on this version of Ubuntu... with commercial software... three cheers for open source on this one... ](*,)

---

