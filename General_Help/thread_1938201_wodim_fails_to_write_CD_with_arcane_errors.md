---
title: "wodim fails to write CD with arcane errors"
date: 2012-03-09
forum: General Help
---

### Post by wvxvw on 2012-03-09
Hello. I've been trying to write an ISO image to CD (upgrading Ubuntu), but wodim fails to write a disc, giving me the following error:

```
sudo wodim -data -raw96r dev=/dev/cdrom speed=16 ~/Downloads/ubuntu-11.10-desktop-amd64.iso 
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDDVDW SH-S202J '
Revision       : 'SB01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 2823 KB/s
Starting to write CD/DVD at speed  16.0 in real RAW/RAW96R mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 15.803s timeout 60s
wodim: OPC failed.
```

I'm not sure I ever used this CD drive to successfully record CDs. Even if I did, then it would be few years ago - which means the software and drivers might've been updated since then.

I read at some other forums that wodim isn't perfect for the task, but I couldn't find any alternative (all the GUI programs I tried actually use it behind the stage, so I'm getting just the same error, as I would otherwise).

Anything else I could try?
Thanks in advance.

---

### Post by Jon Monreal on 2012-03-09
> I read at some other forums that wodim isn't perfect for the task, but I couldn't find any alternative (all the GUI programs I tried actually use it behind the stage, so I'm getting just the same error, as I would otherwise).

You might try cdrskin to see if it's just wodim that is producing the error.

---

