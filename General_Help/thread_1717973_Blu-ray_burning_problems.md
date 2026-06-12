---
title: "Blu-ray burning problems"
date: 2011-03-30
forum: General Help
---

### Post by aSmig on 2011-03-30
I have yet to successfully burn a Blu-ray disc.  Do you have a success story you would care to share?  Drive and media specifications, commands used, and any other useful insight would be greatly appreciated.  Here is an overview of what I have tried:

First, I create the image:
```
$ genisoimage -graft-points -allow-limited-size -iso-level 2 -J -r -input-charset utf-8 -Vstuff -udf -o stuff.iso OneReallyBig.tar
```And this seems fine.  I can mount the iso, verify checksums, all is well.  So now I have an iso that is about 8.5GB, ready to burn.

```
$ wodim -verbose -ignsize -tao speed=2 dev=/dev/sr1 stuff.iso 
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr1'
devname: '/dev/sr1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ATAPI   '
Identification : 'iHBS112   2     '
Revision       : 'CL04'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0041 (BD-R sequential recording)
Profile: 0x0043 (BD-RE) 
Profile: 0x0042 (BD-R random recording) 
Profile: 0x0041 (BD-R sequential recording) (current)
Profile: 0x0040 (BD-ROM) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 6094848 = 5952 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data  8672 MB        
Total size:     9959 MB (986:44.37) = 4440328 sectors
Lout start:     9960 MB (986:46/28) = 4440328 sectors
Current Secsize: 2048
  ATIP start of lead in:  -150 (00:00/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
wodim: Cannot get next writable address for 'invisible' track.
wodim: This means that we are checking recorded media.
wodim: This media cannot be written in streaming mode anymore.
wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
wodim: ERROR: Could not manage to find medium size, and more than 8.0 GB of data.
wodim: Cannot write more than remaining DVD capacity.
$
```Okay, I read that cdrecord/wodim is full of complex politics.  It's not a huge surprise that some things like identifying larger capacity media such as Blu-ray has slipped through the cracks. I would have expected the -ignsize flag to help here, but no dice.  The good news is that nothing has been written to the disc yet, so it isn't a coaster yet.  If cdrkit can't recognize the media, then I should check dvd+rw-tools, says the Internet.

```
$ dvd+rw-mediainfo /dev/sr1
INQUIRY:                [ATAPI   ][iHBS112   2     ][CL04]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         41h, BD-R SRM+POW
 Media ID:              VERBAT/IMw
 Current Write Speed:   2.0x4495=8990KB/s
 Write Speed #0:        2.0x4495=8990KB/s
 Speed Descriptor#0:    00/12219391 R@6.0x4495=26970KB/s W@2.0x4495=8990KB/s
POW RESOURCES INFORMATION:
 Remaining Replacements:16843040
 Remaining Map Entries: 0
 Remaining Updates:     0
READ DISC INFORMATION:
 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ FORMAT CAPACITIES:
 unformatted:           12219392*2048=25025314816
 00h(3000):             11826176*2048=24220008448
 32h(0):                11826176*2048=24220008448
 32h(0):                5796864*2048=11871977472
 32h(0):                12088320*2048=24756879360
READ TRACK INFORMATION[#1]:
 Track State:           invisible incremental
 Track Start Address:   0*2KB
 Next Writable Address: 0*2KB
 Free Blocks:           12219392*2KB
 Track Size:            12219392*2KB
 Last Recorded Address: 0*2KB
READ CAPACITY:          0*2048=0
$
```Sure enough, that looks like the blank 25GB disc I put in the tray.  So maybe the dvd+rw-tools growisofs utility will have better luck at burning...

```
$ growisofs -speed=1 -dvd-compat -Z /dev/sr1=stuff.iso
Executing 'builtin_dd if=stuff.iso of=/dev/sr1 obs=32k seek=0'
/dev/sr1: pre-formatting blank BD-R for 24.8GB...
/dev/sr1: "Current Write Speed" is 2.0x4390KBps.
:-[ WRITE@LBA=0h failed with SK=5h/LOGICAL BLOCK ADDRESS OUT OF RANGE]: No space left on device
:-( write failed: No space left on device
$
```Now I have a coaster.  Specifically, dvd+rw-mediainfo tells me that the Disc status is appendable rather than blank, and lists various track information.  And when I reload the media, I end up with...

```
$ dvd+rw-mediainfo /dev/sr1
INQUIRY:                [ATAPI   ][iHBS112   2     ][CL04]
GET [CURRENT] CONFIGURATION:
:-( no media mounted, exiting...
$
```And that isn't just because I haven't waited long enough for the disc to read.  It gives me this output at 1, 5, 30, 60, and 480 minutes after tray load.  Oh, I have also gotten the same flavor of failure by letting growisofs build the iso on the fly, using:

```
growisofs -speed=1 -Z /dev/sr1 -R -J OneReallyBig.tar
```I have worked through a number of other approaches, but figure this post is long enough as is.  Feel free to ask for clarification or more details on anything.  Any suggestions or descriptive success stories would be appreciated.  Thanks!

---

### Post by schily on 2011-03-31
Wodim does not support to write DVDs or BluRays. Background: the original working DVD driver from the original cdrecord has been removed and replaced by something that does not work. A BluRay driver is not present. The state of wodim is otherwise like a cdrecord from September 2004 + additional bugs e.g. in the SCSI transport.

Wodim is also full of license problems and Debin decided to attack the cdrtools project - unfortunately Mr. Shuttleworth followed this attack and does not include the original software even though he promised to do so in 2008.

The good news: cdrecord/cdrtools (the original software) is still available, has been reviewed by lawyers to be free of license problems and is actively maintained. The original software includes working BluRay support since 2007.

See:
[ftp://ftp.berlios.de/pub/cdrecord/alpha/](ftp://ftp.berlios.de/pub/cdrecord/alpha/)

or the Ubuntu packages from frustrated Ubuntu users (search e.g. for Brandon Snider - I hope I made no typo).

---

### Post by SeijiSensei on 2011-03-31
K3b apparently [supports]("http://k3b.plainblack.com/") Blu-ray drives.

> With a few exceptions, K3b [2.0] keeps feature-parity with 1.0.x series, but it also introduces a number of new features. Perhaps the biggest among these is support for Blu-ray drives.

Who knows? Maybe you'll like K3b so much you'll ditch GNOME and join with us KDE users.

---

### Post by ghat on 2011-03-31
hi

I am in the same boat... 

I have files from my avchd camcorder which I want to back up at a remote location, (I already have 2 HDD copies in the home). After a ot f research I understand Bluray is the way to go (actually BDXL, but the hardware and media is prohibitively expensive for me)

My solution is a LG BDRW drive with LTH support, LTH discs are cheaper.. I am still looking for Taiyo yuden in the US, 
([http://www.cdrinfo.com/sections/news/Details.aspx?NewsId=24806](http://www.cdrinfo.com/sections/news/Details.aspx?NewsId=24806))
which is by far the most archival safe brand/manufacturer if you don't what to shell out your hard cash on those gold media... 

So, I just tested Nero-Linux-4 yesterday, (eval/free version) and burning the 23GB of m2ts files was a piece of cake... 

I used the UDF only filesystem, as I understand the joliet/iso stuff has issues with large files.  I have very large m2ts (>4GB) files on the disk. also the geniso manpage tells that UDF support in it is in alpha (ubuntu maverick version)

Next I want to use actually create a 19GB only or so ISO image for each disk I want to burn and and then use dvdisaster to generate ECC for the 19GB iso which will make it hopefully less than the 23.867GB size of my verbatim BDR-LTH disks.

The thing to now see is how this UDF works with dvdisaster, will the nero-udf be compatible ? or I will have to figure out some hack. I am hesitant to use genisoimage, and not sure if udftools can be used in some way in this scenario...

BTW, I guess if my experiment works, I am pretty much going to buy the nero-linux for $20/-, as bd-r burning definitely works with it...

g
> 
this is from man genisoimage

```

       -allow-limited-size
              When  processing  files  larger than 2GiB which cannot be easily represented in ISO9660, add them with a shrunk visible
              file size to ISO9660 and with the correct visible file size to the UDF system. The result is an inconsistent filesystem
              and  users  need to make sure that they really use UDF rather than ISO9660 driver to read a such disk. Implies enabling
              -udf.


   -udf   Include UDF filesystem support in the generated filesystem image.  UDF support is currently in  alpha  status  and  for
              this  reason,  it  is  not possible to create UDF-only images.  UDF data structures are currently coupled to the Joliet
              structures, so there are many pitfalls with the current implementation. There is no UID/GID support, there is no  POSIX
              permission  support, there is no support for symlinks.  Note that UDF wastes the space from sector ~20 to sector 256 at
              the beginning of the disc in addition to the space needed for real UDF data structures.

```

You will have to use UDF if you have files >2GB and then UDF support is 'alpha' so I am not sure if we can really burn a proper BD. I am not really sure
what nero uses, but it seems to be working for a normal burn. The only glitch is that it by itself cannot make image files > 16GB, so it splits the image...

still working on it.. 



---

### Post by schily on 2011-04-01
Genisoimage has general problems with large files. It is based on a mkisofs from September 2004 that was limited to 4 GB. Note that genisoimage has various issues in UDF that have been removed in 2007 in the original mkisofs.

The original mkisofs has seen major improvements since 2004 with respect to many features. It supports files up to 8 TB (if you specify -iso-level 3 or above), it implements error control for backups, it allows to use find(1) like arguments via libfind, it implements UDF permissions and arbitrary file types with UDF, .......

See: [http://cdrecord.berlios.de/private/man/cdrecord/mkisofs.8.html](http://cdrecord.berlios.de/private/man/cdrecord/mkisofs.8.html)

If you prefer to run a Linux kernel from 2004, you may continue running genisoimage, but of you like up to date software, you should consider to upgrade to recent original cdrtools.

---

### Post by ghostborg on 2011-06-16
I agree back to Nero for now, I was able to burn some bluray but K3b stops just before verifying and tells me Fatal Error. Nice. Home video to precious to risk sketchy burns.

---

