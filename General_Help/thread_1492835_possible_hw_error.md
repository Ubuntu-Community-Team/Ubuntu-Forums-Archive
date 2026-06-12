---
title: "possible hw error ?"
date: 2010-05-25
forum: General Help
---

### Post by ub007 on 2010-05-25
Hi ,

I've got a Tape drive attached to my server connected by SAS card, and am trying to copy some data across.

but it fails to write, in dmesg i see

> scsi 1:0:1:0: Attached scsi generic sg1 type 1
mptbase: ioc0: LogInfo(0x31120403): Originator={PL}, Code={Abort}, SubCode(0x0403)


does this mean faulty hardware/cables?

thanks in advance
david

---

### Post by badger_fruit on 2010-05-25
After performing a quick google search it's quite a common error; the device seems to be recognised and just that the OS is having trouble writing to it.  perhaps try a replacement cable first, then replacement card and elimiate the possible causes of the problem one by one.

Good luck.

---

