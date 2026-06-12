---
title: "SuperMicro AOC-SASLP-MV8 Issues"
date: 2012-05-07
forum: General Help
---

### Post by nasha on 2012-05-07
Hi all,

Hoping someone can offer some advice with this card under Linux.

**Issue:**
The drives were listed in /dev/ but i could not access the drives at all - It would say the FS was bad. **This only occurs when connecting my previous mdadm array drives.** Connecting new unformatted drives, i am able to format them and add them to the array ok.

dmesg was full of the following (for all connected drives):
 30.944490] sd 5:0:2:0: [sdd] Unhandled error code
[   30.944500] end_request: I/O error, dev sdd, sector 0
[   30.944527] sd 5:0:2:0: [sdd] Unhandled error code
[   30.944536] end_request: I/O error, dev sdd, sector 0
[  310.049446] ata12: sas eh calling libata cmd error handler
[  310.049449] ata7: sas eh calling libata port error handler
[  310.049460] ata8: sas eh calling libata port error handler
[  310.049465] ata9: sas eh calling libata port error handler

[ 1300.469247] /build/buildd/linux-3.0.0/drivers/scsi/mvsas/mv_sas.c 2198:port 6 ctrl sts=0x199800.
[ 1300.469250] /build/buildd/linux-3.0.0/drivers/scsi/mvsas/mv_sas.c 2200:Port 6 irq sts = 0x1000000


Running version 3.04.19 of mtpsas.

Have confirmed this card is working under Windows.

Thoughts or suggestions anyone?

Thanks,
Nash

---

