---
title: "Burning Problems"
date: 2011-01-17
forum: General Help
---

### Post by hansum_rahul on 2011-01-17
Brasero fills my dvd with **nulls** (**Zeros**)... It seems to work but checksum always tells me about the failure...

However, once when I burned just 1 file... it burned okey (it was a text file)...

I was burning many files together... always >700-800Megs... and everytime I burned to disk... I would get the files burnt but... they would be full of **zeros** (0)... **NULL bytes**...

What is wrong??

I tried GnomeBaker... it did burn successfully.. but it cannot burn multi-session... I get a host of errors...

First error with GnomeBaker: mount point not found.. so I added a mount point in /etc/fstab :-
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

```
and then the next error... could not find /media/cdrom0

So I did this:

```
sudo mkdir /media/cdrom0

```
Then the multi-session was imported, but when I begin to burn... I get errors that means that the mounted files are not found... Maybe I cannot burn directly to disk?

Now third try, K3B
K3B fails to burn multi-session... 

This is the full log of K3B:-
```

Devices
-----------------------
HP DVD Writer 1135r LH25 (/dev/sr1, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]
HL-DT-ST DVD-RAM GSA-H55N 1.05 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 102606 (210137088 bytes)

System
-----------------------
K3b Version: 2.0.1
KDE Version: 4.5.1 (KDE 4.5.1)
QT Version:  4.7.0
Kernel:      2.6.35-24-generic

Used versions
-----------------------
mkisofs: 1.1.10
cdrecord: 1.1.10

cdrecord
-----------------------
scsidev: '/dev/sr1'
devname: '/dev/sr1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Waiting for data on stdin...
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HP      '
Identification : 'DVD Writer 1135r'
Revision       : 'LH25'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1310720 = 1280 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 22160 KB/s
Track 01: data   200 MB        
Total size:      230 MB (22:48.08) = 102606 sectors
Lout start:      230 MB (22:50/06) = 102606 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Starting to write CD/DVD at speed  17.0 in real SAO mode for multi session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 01 90 CE 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x05 (no more track reservations allowed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.005s timeout 200s
/usr/bin/wodim: Cannot open new session.
input buffer ready.
Writing  time:    8.225s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr1 speed=16 -sao driveropts=burnfree -multi -waiti -data -tsize=102606s -

mkisofs
-----------------------
Rock Ridge signatures found
102606
I: -input-charset not specified, using utf-8 (detected in locale settings)
Rock Ridge signatures found
 94.97% done, estimate finish Mon Jan 17 15:05:48 2011
 95.00% done, estimate finish Mon Jan 17 15:05:48 2011
 95.02% done, estimate finish Mon Jan 17 15:05:48 2011
 95.05% done, estimate finish Mon Jan 17 15:05:48 2011
 95.07% done, estimate finish Mon Jan 17 15:05:48 2011
 95.10% done, estimate finish Mon Jan 17 15:05:48 2011
 95.12% done, estimate finish Mon Jan 17 15:05:48 2011
 95.15% done, estimate finish Mon Jan 17 15:05:48 2011
 95.17% done, estimate finish Mon Jan 17 15:05:48 2011
 95.19% done, estimate finish Mon Jan 17 15:05:48 2011
 95.22% done, estimate finish Mon Jan 17 15:05:48 2011
 95.24% done, estimate finish Mon Jan 17 15:05:48 2011

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -cdrecord-params 138224,1933744 -prev-session /dev/sr1 -gui -graft-points -print-size -quiet -volid GnomeBaker data disk -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-rahul/k3beo4841.tmp -rational-rock -hide-list /tmp/kde-rahul/k3bqH4841.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-rahul/k3bJv4841.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -cdrecord-params 138224,1933744 -prev-session /dev/sr1 -gui -graft-points -volid GnomeBaker data disk -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-rahul/k3bPS4841.tmp -rational-rock -hide-list /tmp/kde-rahul/k3bNY4841.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-rahul/k3bGm4841.tmp

```


Now, I tried to replace wodim with cdrtools... with this repository:

[https://launchpad.net/~brandonsnider]("https://launchpad.net/~brandonsnider")

I tried again with both brasero and K3B and I get similar errors...

---

### Post by hansum_rahul on 2011-01-17
And now I am out of dvds to experiment again :mad:

---

### Post by hansum_rahul on 2011-01-17
I found these bugs:

[URL="https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076"]https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076
[/URL]
And I just discovered this thread:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1650722]("http://www.uluga.ubuntuforums.org/showthread.php?t=1650722")


Let me buy some disks this evening...

---

