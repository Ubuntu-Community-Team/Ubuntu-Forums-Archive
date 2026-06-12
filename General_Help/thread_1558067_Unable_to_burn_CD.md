---
title: "Unable to burn CD"
date: 2010-08-21
forum: General Help
---

### Post by J Bratton on 2010-08-21
Hi folks- I'm running Lucid Lynx and have been trying to burn an MP3 file to a CD-R so I could listen to it in my car. I've tried Brasero, CD/DVD creator, KB3, GnomeBaker, and VLC, and all of them failed in one way or another. Since Brasero comes stock and people have more experience with that one, I think I might describe the troubles with it. 

What happens is that it doesn't seem to recognize the blank medium inserted. I open a project (either Audio CD or Data CD), add the files I want to burn. Then it says, "Please insert a writable CD or DVD if you do not want to write to an image file." I insert a blank CD-R, and it spins it, but nothing changes. The pulldown at the bottom still only gives me the choice of writing an image file. No recognition that the blank medium has been inserted and that that is where I want to burn the file. When I hit the 
"burn" button, it opens a dialog box, asking me where I want to locate the image file it has called "brasero.cue"

Not sure how to do further troubleshooting on this.

When I tried the same thing in GnomeBaker, I got an error message saying the burning has failed. Here's the log file from that:



wodim: No write mode specified. 
wodim: Assuming -tao mode. 
wodim: Future versions of wodim may have different drive dependent defaults. 
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits. 
scsidev: '/dev/sr0' 
devname: '/dev/sr0' 
scsibus: -2 target: -2 lun: -2 
Linux sg driver version: 3.5.27 
Wodim version: 1.1.10 
SCSI buffer size: 64512 
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device 
communication breaks or freezes immediately after that. 
TOC Type: 0 = CD-DA 
Device type    : Removable CD-ROM 
Version        : 5 
Response Format: 2 
Capabilities   : 
Vendor_info    : 'TSSTcorp' 
Identification : 'CD/DVDW TS-H652M' 
Revision       : '0414' 
Device seems to be: Generic mmc2 DVD-R/DVD-RW. 
Current: 0x0000 (Reserved/Unknown) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
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
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R 
Drive buf size : 57376 = 56 KB 
FIFO size      : 12582912 = 12288 KB 
Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error 
CDB:  00 00 00 00 00 00 
status: 0x2 (CHECK CONDITION) 
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 01 00 00 
Sense Key: 0x2 Not Ready, Segment 0 
Sense Code: 0x3A Qual 0x01 (medium not present - tray closed) Fru 0x0 
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s 
wodim: No disk / Wrong disk! 

=======================================================
The burner works fine (as tested in Windows), and it reads CDs and DVDs no problem. I just can't get the burning to complete correctly. I have installed the restricted extras. I'm not really concerned WHICH program I use, I'd just like to be able to burn a CDs for road trips and whatnot.
thanks in advance!
John

---

### Post by drdanielfc on 2010-08-21
Does ubuntu recognize the blank disk in nautilus?

---

### Post by J Bratton on 2010-08-22
> **drdanielfc said:**
> Does ubuntu recognize the blank disk in nautilus?
I'm not sure. If I go to Places- Computer, then I can see the CD/DVD drive listed. But there isn't anything else I can see. Should it say, "blank media" or something like that somewhere?
thx
EDIT: Using K3b, it appears that it is NOT recognizing the blank disc at all. In both Brasero and K3b it looks like there is a pulldown where blank media should appear during the burning process and this is not happening.

I thought that maybe this might have to do with how my Western Digital external usb hard drive has a bit of $%$#%%$# that shows up as a CD drive, even though it is just a piece of annoying firmware from WD. But, shutting down, removing the WD USB drive, and restarting didn't help the process. No blank CD-R recogized. Doesn't recogize a CD-RW, either....

---

### Post by J Bratton on 2010-08-23
> **J Bratton said:**
> I'm not sure. If I go to Places- Computer, then I can see the CD/DVD drive listed. But there isn't anything else I can see. Should it say, "blank media" or something like that somewhere?
thx
EDIT: Using K3b, it appears that it is NOT recognizing the blank disc at all. In both Brasero and K3b it looks like there is a pulldown where blank media should appear during the burning process and this is not happening.

I thought that maybe this might have to do with how my Western Digital external usb hard drive has a bit of $%$#%%$# that shows up as a CD drive, even though it is just a piece of annoying firmware from WD. But, shutting down, removing the WD USB drive, and restarting didn't help the process. No blank CD-R recogized. Doesn't recogize a CD-RW, either....
And, oddly enough, it seems to recognize and burn blank DVD-RWs just fine. Problem is, I can't play DVDs in my car...

---

### Post by dunnac on 2010-08-31
I'm having the same problem. Back to Hardy methinks.

---

### Post by dunnac on 2010-08-31
It seems that Lucid is unable to burn mp3 files. If you convert them to wav files (using sound converter from synaptics), they will burn. Full instructions at [http://www.ehow.com/how_5066158_convert-mp-wav-ubuntu.html](http://www.ehow.com/how_5066158_convert-mp-wav-ubuntu.html).

---

