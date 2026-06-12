---
title: "The best cd burner for Linux"
date: 2009-07-30
forum: General Help
---

### Post by fernandoc1 on 2009-07-30
I'm having lots of trouble to erase a CD-RW in Ubuntu Jaunty. I have tried GnomeBaker K3b and Brasero until now, and none has erased my CD.
There is no problem with the CD, because after I got exhausted of trying erase the disk on Linux, I went to Windows and erased the disk and burned an ISO that is working perfectly.
So I don't think that is a problem with the hardware.
Can someone help me find whats is going on. I always face this problem on Ubuntu, and I'm worried about it, because this is an simple task that should be supported by Ubuntu and its sounds that it isn't.

---

### Post by Katalog on 2009-07-30
I like Brasero, but it has been know to have a few hiccups when erasing disks. To erase a CD-RW in Linux, open the terminal and run the following commands:

```
umount /dev/cdrom
```then 
```

cdrecord dev=/dev/cdrom blank=fast
```and see if that doesn't work for you.

---

### Post by fernandoc1 on 2009-07-30
this is what happened when I tried the commands that you told me.

```
fernando@fernando-desktop:~$ umount /dev/cdrom
fernando@fernando-desktop:~$ cdrecord dev=/dev/cdrom blank=fast
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RAM GSA-H55N'
Revision       : '1.02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 1764 KB/s
Starting to write CD/DVD at speed  10.0 in real BLANK mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 09 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 10.253s timeout 9600s
wodim: Cannot blank disk, aborting.
wodim: Some drives do not support all blank types.
wodim: Try again with wodim blank=all.
fernando@fernando-desktop:~$
```

---

### Post by Katalog on 2009-07-31
I'm not that sharp when it comes to command line output and can't really tell with any degree of certainty what the error was that occurred there. Hopefully someone smarter than myself will happen by and be able to decipher what all that output means.

I know that you've already tried the top three CD Burning apps, so have you considered that perhaps your burner hardware is just not well supported in Linux? Just a thought.

---

