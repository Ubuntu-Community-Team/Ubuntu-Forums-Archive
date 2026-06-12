---
title: "Odd problem: mount: special device /dev/scd0 does not exist"
date: 2011-01-09
forum: General Help
---

### Post by bobnutfield on 2011-01-09
Hello everyone,

I have been trying to breath some new life into an old P4 desktop that was an ex-security camera control box from my company.  They were just going to throw it away, so I took it home and put Lucid on it.  It has three hard drives, each 500GB, with one Primary and two secondary.  They are all IDE.  When I tried to run a live CD in the Sony DVD drive, it would get to a start screen, then fail with "Cannot find media with a kernel." Which of course meant that the CD drive with the live CD could not be read.  This same result happened with every live CD I tried EXCEPT Ubuntu 9.04, which I went ahead and installed, then upgraded online all the way to Lucid.  Everything has been working fine, quick and snappy.

However, I tried to put a DVD in the drive and discovered it was not recognized as even existing.  wodim -scanbus command yielded this:

```
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation
``` 

Clicking on the icon in the Computer location of the desktop resulted in the error in the title of this thread.

So, I checked to make the BIOS recognized it.  It did, and it is connected as an IDE Primary Slave.  I tried moving the jumpers around to make it a master or cable select, and unless it is connected as a slave, the BIOS won't recognize it.

Can anyone offer an clue what this might be?  I know the device is function as it installed Jaunty fine and does run other live cd's to the point of selecting run.  This must be the same issue that does not allow the other live cd's to find the kernel.

Thanks in advance for any thoughts or help

Bob

---

### Post by bobnutfield on 2011-01-09
No one has ever encountered a non-existing cd rom drive?  It does not show up in dmesg and there is no entry for it in fstab.  Anyone with a clue?

---

### Post by tredegar on 2011-01-09
You say it is old hardware. The drive / cable is probably failing / broken.
Try replacing it with another.

---

### Post by bobnutfield on 2011-01-09
Thank you for your reply.  I finally got it to be recognized in dmesg:

> [    2.197518] ata1.01: ATAPI: SONY    DVD RW DW-Q28A, KYS2, max UDMA/66
[    2.197558] ata1.00: limited to UDMA/33 due to 40-wire cable
[    2.197563] ata1.01: limited to UDMA/33 due to 40-wire cable
[    2.213367] ata1.00: configured for UDMA/33
[    2.229201] ata1.01: configured for UDMA/33
[    2.252574] isapnp: No Plug & Play device found
[    2.252750] scsi 0:0:0:0: Direct-Access     ATA      HDS725050KLAT80  K2AO PQ
: 0 ANSI: 5
[    2.252941] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 
GiB)
[    2.253014] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.253053] sd 0:0:0:0: [sda] Write Protect is off
[    2.253061] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.253110] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[    2.253952] scsi 0:0:1:0: CD-ROM            SONY     DVD RW DW-Q28A   KYS2 PQ
: 0 ANSI: 5
[    2.256021] sr0: scsi3-mmc drive: 125x/125x writer cd/rw xa/form2 cdda tray
[    2.256026] Uniform CD-ROM driver Revision: 3.20

Not I just need it to be automatically mounted when media is inserted.  The /dev/cdrom is symlinked with sr0.  I probably just need to edit fstab and reboot.

I had considered the fact that it may indeed be that the drive had failed, but it is being seen in the bios and the live cd's do boot to a screen.

I just now tried to manually mount the /dve/cdrom directly and it worked.  Just need to automate it now.

Thanks

Bob

---

