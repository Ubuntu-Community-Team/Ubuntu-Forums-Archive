---
title: "Jaunty Freezes when insert any CD"
date: 2009-08-27
forum: General Help
---

### Post by jazzmes on 2009-08-27
I'm running jaunty and each time I insert a CD on my drive it freezes...
Is there a way to troubleshoot these type of CD/DVD problems?

My DVD RW...
Aug 27 14:25:14 vicente kernel: [    3.952446] ata7.00: ATAPI: **Optiarc DVD RW AD-7173A**, 1-03, max UDMA/66
Aug 27 14:25:14 vicente kernel: [    3.968337] ata7.00: configured for UDMA/66
Aug 27 14:25:14 vicente kernel: [    4.136522] scsi 6:0:0:0: CD-ROM            Optiarc  DVD RW AD-7173A  1-03 PQ: 0 ANSI: 5
Aug 27 14:25:14 vicente kernel: [    4.139046] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 27 14:25:14 vicente kernel: [    4.139050] Uniform CD-ROM driver Revision: 3.20
Aug 27 14:25:14 vicente kernel: [    4.139170] sr 6:0:0:0: Attached scsi CD-ROM sr0
Aug 27 14:25:14 vicente kernel: [    4.139215] sr 6:0:0:0: Attached scsi generic sg1 type 5


Thanks,
Tiago

---

### Post by SPr on 2009-08-27
Wait a minute or two to decide whether it's a lock up or lack of patience.

ctrl+alt+f1
Login
Insert cd
Wait while CD spins up.
```

dmesg|tail

```

---

### Post by arunsub on 2009-09-02
I have the same Optiarc AD-7173A. My system also hangs when I insert a CD. The only way I could get around is to uninstall Brasero and install GNome baker. I don't know how it's related, but it works.

---

