---
title: "SCSI cdrom deactivates after disk removal"
date: 2009-08-12
forum: General Help
---

### Post by rpm2hi on 2009-08-12
Yes, it's true.  I actually have a *SCSI* CD burner...
 
Background: Hardy system with 2 optical drives
Drive -1 =ATAPI DVD-ROM (/dev/cdrom)
Drive -2 = SCSI CD-R/RW  (/dev/cdrom1)

If the computer is booted with a data CD in the ATAPI and SCSI drives, they both mount and work ok with no apparent problem or message in syslog.

 The problem occurs:
1. If no disk is in the ATAPI drive, but only in the SCSI drive when booting or
2. If no disk in in either drive when booted or
3. A short period of time after the SCSI disk is ejected

Failure Action: The kernel starts spitting out this error message about every 2 seconds about the scsi disk: "kernel: [29054.517304] (scsi2:A:3:0): Unexpected busfree in Message-out phase".  Once the message starts, a new disc will not mount in the drive without reboot.
 
I don't believe that this is a hardware issue, as both drives work correctly if booted with disks in them.

I would really appreciate someone with removable disk / cd drive configuration experience to consider this issue, and give me a clue.

Let me know if you want any config files included in this post.

Thanks!

rpm2hi

---

### Post by cariboo on 2009-08-13
I've got an external scsi burner, it isn't connected to my G3, if you can wait until later on tomorrow, I can hook it up and see if I can duplicate your problem.

---

### Post by rpm2hi on 2009-08-13
> **cariboo907 said:**
> I've got an external scsi burner, it isn't connected to my G3, if you can wait until later on tomorrow, I can hook it up and see if I can duplicate your problem.

Thanks--  The system is happy as long as I keep a non-blank disk in each drive.

---

### Post by cariboo on 2009-08-13
I tried several different scsi drives, and can't replicate your problem. I tried an external CD/RW drive, a 6 Disc changer and an external CD drive. The only thing I managed to do was report a bug for mybashburn. The computer has an internal DVD drive and the external devices were the last device on the cable and a terminator is installed. I even tried with all the drives daisy chained, and still no joy.

The only thing I can suggest is to make sure the cable is OK and that the drive is terminated properly.

---

### Post by rpm2hi on 2009-08-14
> **cariboo907 said:**
> I tried several different scsi drives, and can't replicate your problem. I tried an external CD/RW drive, a 6 Disc changer and an external CD drive. The only thing I managed to do was report a bug for mybashburn. The computer has an internal DVD drive and the external devices were the last device on the cable and a terminator is installed. I even tried with all the drives daisy chained, and still no joy.
 
The only thing I can suggest is to make sure the cable is OK and that the drive is terminated properly.
 
Thanks for all your testing!
 
 
 
The thing that's strange with my system is that even on booting, the scsi drive is ignored unless I put a disc in the ATAPI drive also. I haven't checked if the ATAPI drive will accept a disk after booting even if the SCSI drive is in a fail condition.

---

