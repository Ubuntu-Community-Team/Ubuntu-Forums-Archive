---
title: "CD/DVD Drive Unable To Eject"
date: 2012-08-12
forum: General Help
---

### Post by Shadius on 2012-08-12
Hey everybody! :)

My CD/DVD drive is unable to eject. I've pressed the eject button a million times, but it won't open. It makes a sound like it wants to open, but doesn't. I've also tried the "eject" command via Terminal. This is what I get:

```
shadius@shadius-asus:~$ eject --verbose
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/sr0'
eject: `/dev/sr0' is not mounted
eject: `/dev/sr0' is not a mount point
eject: `/dev/sr0' is not a multipartition device
eject: trying to eject `/dev/sr0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: trying to eject `/dev/sr0' using SCSI commands
eject: SCSI eject failed
eject: trying to eject `/dev/sr0' using floppy eject command
eject: floppy eject command failed
eject: trying to eject `/dev/sr0' using tape offline command
eject: tape offline command failed
eject: unable to eject, last error: Inappropriate ioctl for device
shadius@shadius-asus:~$ 

```

The only method I have to open the CD/DVD tray is to manually open it with a pin. I'm wondering what the "Inappropriate ioctl for device" means, or if this is a sign of a failing CD/DVD drive. Please help me diagnose and solve this issue. Thank you in advance.

---

### Post by sienile on 2012-08-12
During POST can you eject the tray using the button on the drive? That will rule out an issue with the drive itself. It would then be a software issue.

---

### Post by mc4man on 2012-08-12
By default your cd drive is locked once a disk is inserted & the device button will not work.
You can try this noting it only lasts per session

With **No** disk in the drive run 
```
eject -i 0
```
Then insert a disk & see if it can be ejected with the device button

If so & that's what you want you can maybe change the default (don't know how here) or simply create a start up script to run that command noting the command can only work when the drive is empty

Edit: in the upcoming 12.10 I believe that command will have no effect

---

### Post by Irihapeti on 2012-08-12
I'm having the same or a similar problem. In addition, I can put a disk in the drive, it attempts to spin up but isn't recognised by the system.

If I run cdrecord -atip (trying to check the disk in the drive) I get:
```

Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
wodim: Cannot do inquiry for CD/DVD-Recorder.
Errno: 5 (Input/output error), test unit ready scsi sendcmd: fatal error
CDB:  00 00 00 00 00 00
cmd finished after 0.000s timeout 40s

```

So far, the only thing that will fix it is rebooting, which has worked consistently every time.

It is an older drive, but I'm reluctant to go out and buy a new one if the problem is software-related.

---

### Post by sienile on 2012-08-12
> **Irihapeti said:**
> I'm having the same or a similar problem. In addition, I can put a disk in the drive, it attempts to spin up but isn't recognised by the system.

If I run cdrecord -atip (trying to check the disk in the drive) I get: ....

Have you tried running that same command when the drive is working properly?

Given that the problem is resolved by rebooting, it's very possible that it's software related, but I did have a dying drive that acted similarly many years ago. I was using Windows 98se at the time, so I have no way to know what errors to look for in linux.

---

### Post by Irihapeti on 2012-08-12
> **sienile said:**
> Have you tried running that same command when the drive is working properly?

With NO disk in the drive, I get:

```
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-H42L '
Revision       : 'SL00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 BB 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 40s
wodim: No disk / Wrong disk!
```

With a multi-session DVD-RW in the drive, I get:

```
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-H42L '
Revision       : 'SL00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
```

Actually, I generally use cdrskin instead of cdrecord, and I've used the output of cdrskin -atip in scripts to check that I have the right kind of disk.

---

### Post by Shadius on 2012-08-24
> **mc4man said:**
> By default your cd drive is locked once a disk is inserted & the device button will not work.
You can try this noting it only lasts per session

With **No** disk in the drive run 
```
eject -i 0
```
Then insert a disk & see if it can be ejected with the device button

If so & that's what you want you can maybe change the default (don't know how here) or simply create a start up script to run that command noting the command can only work when the drive is empty

Edit: in the upcoming 12.10 I believe that command will have no effect

Didn't work.

---

### Post by Shadius on 2012-08-24
> **sienile said:**
> During POST can you eject the tray using the button on the drive? That will rule out an issue with the drive itself. It would then be a software issue.

If I've done it correctly, the drive didn't open. Just to be sure that I've tried it during POST, POST is when the motherboard splash screen shows up, right? In my case, It shows my ASUS P5P800. It also beeps.

---

### Post by Shadius on 2012-08-25
Still no solution to this problem.

---

### Post by Shadius on 2012-08-29
Bump

---

