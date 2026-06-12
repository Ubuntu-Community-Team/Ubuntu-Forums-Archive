---
title: "Burn Multiple discs at once?"
date: 2011-09-03
forum: General Help
---

### Post by Keypen on 2011-09-03
I have searched but have only found the old program Turbojet2 that can burn multiple discs at once.

I am searching after a program that I can choose a .iso file, type in how many discs that I want to burn, with how menu burners and then hit burn.

Is their a program out there that supports multiple burn just as easy as Nero for Windows and Toast 11 for Mac?

---

### Post by Keypen on 2011-09-06
I have been testing TurboJet 2 but it burns in between 0x and 5x even when I have selected 12x.

TurboJet 2 use growisofs and I tested to write the same command for one dvd burner:```
growisofs -dvd-compact -speed=12 use-the-force-luke=tty -Z /dev/sr0=/TO/THE/IMAGE.iso
```It started burning at 5,5x, at 50% it has speed-ed up steady to 10x. At the end it was at around 12x and when finished growisofs said the average speed was 8,7x.

I have tested to burn with two burners with two terminals but the speed again goes down to max 5x, average around 2x. I have no idea way. Hard drives are not limiting, the CPU is a 4x core, 8GB ram.


Is their any other program that can burn .iso files just like growisofs that I can try? It can be programs any program that can run parallel and use one burner per opened program.


Or is this a setting in Ubuntu 11.04 that I have missed? I can burn with great speed with the same hardware under Windows with Nero.

---

### Post by Keypen on 2011-09-13
The hardware in the system is a Gigabyte GA-H57M-USB3 with Sony Optiarc 72x0 Serial ATA burners.

I tested to connect a PATA burner to the integrated PATA port and used TurboJet 2 to burn. I tested to burn two disks, one with SATA and one with PATA burner. The SATA burner was fine at full speed but PATA burner is going in 2-4x.

Their must be a fix to this. With the same hardware I can burn multiple disks at the same time with no problem at all under Windows.

---

### Post by Keypen on 2011-09-13
I now tested with cdrecord in the terminal with SATA and PATA burner.

I started the first ran a cdrecord -scanbus:

```
user@user:~$ cdrecord -scanbus
scsibus0:
    0,0,0      0) 'Optiarc ' 'DVD RW AD-7200A ' '1.09' Removable CD-ROM
    0,1,0      1) *
    0,2,0      2) *
    0,3,0      3) *
    0,4,0      4) *
    0,5,0      5) *
    0,6,0      6) *
    0,7,0      7) *
scsibus6:
    6,0,0    600) 'Optiarc ' 'DVD RW AD-7260S ' '1.01' Removable CD-ROM
    6,1,0    601) *
    6,2,0    602) *
    6,3,0    603) *
    6,4,0    604) *
    6,5,0    605) *
    6,6,0    606) *
    6,7,0    607) *
```I then started burning with the PATA burner:

```
user@user~/Images$ **cdrecord -v dev=0,0,0 THE_IMAGE.iso**
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
WARNING: the deprecated pseudo SCSI syntax found as device specification.
Support for that may cease in the future versions of wodim. For now,
the device will be mapped to a block device file where possible.
Run "wodim --devices" for details.
Linux sg driver version: 3.5.27
Wodim version: 1.1.11
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Optiarc '
Identification : 'DVD RW AD-7200A '
Revision       : '1.09'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001B (DVD+R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) (current)
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
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1310720 = 1280 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data  4478 MB        
Total size:     5143 MB (509:35.36) = 2293152 sectors
Lout start:     5143 MB (509:37/27) = 2293152 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 1952
Speed set to 24930 KB/s
Starting to write CD/DVD at speed  20.0 in real unknown mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01: 4478 of 4478 MB written (fifo 100%) [buf  96%]   6.1x.

Track 01: Total bytes read/written: 4696375296/4696375296 (2293152 sectors).
Writing  time:  691.344s
Average write speed   5.0x.
Min drive buffer fill was 0%
Total of 2 possible drive buffer underruns predicted.
Fixating...
Fixating time:   20.602s
wodim: fifo had 73973 puts and 73973 gets.
wodim: fifo was 0 times empty and 24365 times full, min fill was 52%.
user@user~/Images$
```It went just fine. Around 10% in a started a other terminal window and started burning with the other burner.

```
user@user~/Images$ **cdrecord -v dev=6,0,0 THE_IMAGE.iso**
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '6,0,0'
scsibus: 6 target: 0 lun: 0
WARNING: the deprecated pseudo SCSI syntax found as device specification.
Support for that may cease in the future versions of wodim. For now,
the device will be mapped to a block device file where possible.
Run "wodim --devices" for details.
[B]Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... giving up.
Error trying to open /dev/scd1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd1 exclusively (Device or resource busy)... retrying in 1 second.[/B]
Linux sg driver version: 3.5.27
Wodim version: 1.1.11
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Optiarc '
Identification : 'DVD RW AD-7260S '
Revision       : '1.01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001B (DVD+R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) (current)
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
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1835008 = 1792 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data  4478 MB        
Total size:     5143 MB (509:35.36) = 2293152 sectors
Lout start:     5143 MB (509:37/27) = 2293152 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 1952
Speed set to 27700 KB/s
Starting to write CD/DVD at speed  22.0 in real unknown mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01: 1236 of 4478 MB written (fifo  99%) [buf  96%]   8.6x.
```When the other burning started I got the errors, made Bold, with /dev/scd0 and /dev/scd1 but then started burning. The first, PATA, burning stopped and SATA burned a bit and then stopped. Then the PATA burned a little, then SATA, then PATA. They didnt burn at the same time.

It is like the system use one thing that can only do one thing at the time, burn one DVD at the time. It must be some little setting or command that is wrong or missing.

There is a warning message in the information that says that I should type: wodim --devices

```
user@user~/Images$ wodim --devices
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'    rwrw-- : 'Optiarc' 'DVD RW AD-7200A'
 1  dev='/dev/scd1'    rwrw-- : 'Optiarc' 'DVD RW AD-7260S'
-------------------------------------------------------------------------
```So... Why do cdrecord want to use the PATA burner when I said it should use the SATA burner? Why did it take so long for it to start burning with the SATA burner when it wasnt burning?

It is SOMETHING the burners are sharing to burn the disks but they do not need to share this SOMETHING because in Windows I can burn multiple disks at the same time with no problem. What is this SOMETHING?

---

### Post by Keypen on 2011-09-15
No one have any tips and tricks that may help?

---

### Post by 3rdalbum on 2011-09-15
Burning multiple discs simultaneously has always been slow for me on Linux. I've never had access to Windows to try it there, but I assumed it would be slow there too. That's why I never completed my multi-disc-burner frontend for you to use; it's quicker to burn one disc at a time.

---

### Post by Keypen on 2011-09-15
> **3rdalbum said:**
> Burning multiple discs simultaneously has always been slow for me on Linux. I've never had access to Windows to try it there, but I assumed it would be slow there too. That's why I never completed my multi-disc-burner frontend for you to use; it's quicker to burn one disc at a time.
The speed in Windows is great and Mac OS X when I tested it a short time on the same hardware. It is something in GNU/Linux that makes multiple burn of disks at the same time is very slow.

Thanks for commenting that it is not just me that has this speed problem.

"That's why I never completed my multi-disc-burner frontend for you to use;"
What front end if i may ask?

---

### Post by CMDR:ZOD on 2012-06-23
Get wine and use mutiple instances of Imgburn. Works great for me & great burn speeds to.

---

### Post by thyrihad on 2013-03-05
FYI, it has not been possible to send commands to multiple optical disc drives on Linux since kernel 2.6.26 (~July 2008), due to a change to the way ioctl calls are locked.

IMO this is a large oversight that should have been solved by now, but unfortunately none of the kernel developers seem interested.

There are software and SDKs out there which are capable of simultaneous multiple drive access but I believe they use their own block-level drivers, rather than using the sg (SCSI generic), driver included in the kernel.  They also cost.  A lot :p

I'm still seeking a fix for this in current kernels, but don't hold your breath.

---

### Post by ejtttje2 on 2013-12-02
I just ran into this as well with two USB burners on 12.10.  Also, creating a disk image with mkisofs (reading files from USB drive, writing to an internal IDE drive) brought a burn (growisofs) on one of the burners to a standstill.  However I can calculate md5sums on one DVD drive while burning full speed on the other, so it seems to be a limitation on parallel writes.

There's a similar looking Fedora bug report here [https://bugzilla.redhat.com/show_bug.cgi?id=877470](https://bugzilla.redhat.com/show_bug.cgi?id=877470)
Which references some mailing list threads:
[http://marc.info/?l=linux-scsi&m=135705061804384&w=2](http://marc.info/?l=linux-scsi&m=135705061804384&w=2)
[https://lkml.org/lkml/2012/3/17/34](https://lkml.org/lkml/2012/3/17/34)
It's pretty disappointing such a fundamental issue with parallel disk IO is left to fester.

---

