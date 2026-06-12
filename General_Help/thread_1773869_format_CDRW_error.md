---
title: "format CDRW error"
date: 2011-06-02
forum: General Help
---

### Post by qwertyjjj on 2011-06-02
I am trying to format a CDRW with the disk utility but I get the following error:
**error creating file system: helper exited with exit code 1: cannot open /dev/sr0: Read-only file system**

Any ideas what to do? As far as I knew CDRWs could not be write protected.

---

### Post by johngreth on 2011-06-02
CDRWs cant be "reformatted", they can be blanked.

Brasero can do it or you can take the command here:

[http://www.ubuntugeek.com/ubuntu-tip-how-to-erase-cd-rwdvd-rw.html](http://www.ubuntugeek.com/ubuntu-tip-how-to-erase-cd-rwdvd-rw.html)

Basically, the disk utility is for hard drives, not CDs.

---

### Post by qwertyjjj on 2011-06-03
> **johngreth said:**
> CDRWs cant be "reformatted", they can be blanked.

Brasero can do it or you can take the command here:

[http://www.ubuntugeek.com/ubuntu-tip-how-to-erase-cd-rwdvd-rw.html](http://www.ubuntugeek.com/ubuntu-tip-how-to-erase-cd-rwdvd-rw.html)

Basically, the disk utility is for hard drives, not CDs.

gave the following error:

j@j-Inspiron-9300:~$ cdrecord dev=/dev/cdrom blank=fast
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDRW/DVD TSL462C'
Revision       : 'DE01'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Starting to write CD/DVD at speed   0.0 in real BLANK mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (valid) 
cmd finished after 0.001s timeout 9600s
wodim: Cannot blank disk, aborting.
wodim: Some drives do not support all blank types.
wodim: Try again with wodim blank=all.

---

### Post by johngreth on 2011-06-04
cdrecord thanks that the disk isn't supported by the drive. Also, I think Brasero uses a different command so you should definitely give it a try.

---

### Post by qwertyjjj on 2011-06-04
> **johngreth said:**
> cdrecord thanks that the disk isn't supported by the drive. Also, I think Brasero uses a different command so you should definitely give it a try.

Brasero won;t even read the disc to blank it, just says disc not available.
Ubuntu can read the disc contents though

---

### Post by qwertyjjj on 2011-06-07
anything I can try to use to verify the disc?
I can read the contents just not format it.

j@j-Inspiron-9300:~$ cd /media
j@j-Inspiron-9300:/media$ ls -l
total 38
drwx------ 3 j j  4096 2011-06-07 13:56 8CD3-8342
drwx------ 5 j j 16384 1970-01-01 01:00 E0FD-1813
drwx------ 3 j j   116 2008-06-17 11:59 My Disc
j@j-Inspiron-9300:/media$ dvd+rw-format -force /media
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.1.
:-( unable to open("/media"): Block device required

I tried formatting it with k3b and it just ejects the disc after 1 second. When I put the dic back in the folder shows up with all the original files so it wasn't blanked at all.

Devices
-----------------------
TSSTcorp CDRW/DVD TSL462C DE01 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM) [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R] [%7]

System
-----------------------
K3b Version: 2.0.1
KDE Version: 4.5.5 (KDE 4.5.5)
QT Version:  4.7.0
Kernel:      2.6.35-28-generic

dvd+rw-format
-----------------------
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.1.
:-( mounted media doesn't appear to be DVD±RW, DVD-RAM or Blu-ray

dvd+rw-format command:
-----------------------
/usr/bin/dvd+rw-format -gui -force /dev/sr0

The disc clearly has DVD-RW printed on it :)

---

### Post by linuxinstalledfromhdd on 2011-06-07
It would be easier just to use cd-rs..  They are pretty cheap too. :)  Or dvd-rs..   It looks like you might have to if you can't get this working.

---

### Post by qwertyjjj on 2011-06-09
> **linuxinstalledfromhdd said:**
> It would be easier just to use cd-rs..  They are pretty cheap too. :)  Or dvd-rs..   It looks like you might have to if you can't get this working.

Is that a solution? What if I really really want to use a DVDRW? :)

---

### Post by linuxinstalledfromhdd on 2011-06-09
Sounds like some kind of driver issue, or compatibility issue.  Did you contact the manufacture to see what they have to say?  :p

You can always try an external dvd-rw usb drive.

---

### Post by psusi on 2011-06-09
You don't have a DVD-RW capable drive.

---

### Post by qwertyjjj on 2011-06-13
> **psusi said:**
> You don't have a DVD-RW capable drive.

yep, that would do it, it's only CDRW.
Oops.

---

