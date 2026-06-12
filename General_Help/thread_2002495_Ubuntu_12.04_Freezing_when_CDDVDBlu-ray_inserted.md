---
title: "Ubuntu 12.04 Freezing when CD/DVD/Blu-ray inserted"
date: 2012-06-12
forum: General Help
---

### Post by philm1983 on 2012-06-12
Hi,

I installed ubuntu 12.04 on Sunday, I have updated it completely today (12/6) and so far have installed the following software.

VLC
Virtual Box
Banshee
Google Chrome
Spotify
GIMP

All has been running perfectly up until this afternoon when I tried loading a Blu-Ray movie to see if it would play.  After around 20 seconds the system froze and was unresponsive to keyboard input.  I tried pinging from another machine and again it froze.

I tried a DVD and the same happened again. I also tried the Ubuntu install CD-ROM which worked first time leading me to believe it was a DVD/Blu-ray movie issue, but on trying the Ubuntu CD-ROM a second time, it froze.

There are no errors in the syslog indicating what may of caused this, it appears to freeze before anything can get logged.

This is the info I got about the drive from dmesg | more

[    2.135022] ata8.00: ATAPI: ATAPI   iHOS104, WL0F, max UDMA/100
[    2.135859] ata8.00: configured for UDMA/100
[    2.140298] scsi 7:0:0:0: CD-ROM            ATAPI    iHOS104          WL0F PQ: 0 ANSI: 5
[    2.144196] sr0: scsi3-mmc drive: 32x/32x cd/rw xa/form2 cdda tray
[    2.144201] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.144324] sr 7:0:0:0: Attached scsi CD-ROM sr0
[    2.144384] sr 7:0:0:0: Attached scsi generic sg1 type 5

I have not had chance to test with another drive yet, I am hoping to pick one up tomorrow to test.  

Has anyone had similar issues, or can suggest anything?

Motherboard = Asus P8Z68-M PRO

---

### Post by philm1983 on 2012-06-12
Update - I found an old SATA CD/DVD reader.  Tried with that and still the same.

Decided to try a different SATA port on the motherboard and all seems to be ok now. Still testing but managed to get a DVD movie playing and it seems to be reading fine now with both drives.

:)

---

