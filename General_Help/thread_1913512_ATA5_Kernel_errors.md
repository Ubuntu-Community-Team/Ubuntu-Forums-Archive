---
title: "ATA5 Kernel errors"
date: 2012-01-22
forum: General Help
---

### Post by granjerox on 2012-01-22
Hi,

I'm having performance and hangup problems since a few weeks. I though it could be a HD failure and I bought a new one and reinstalled but the same problem persists. I'm using Ubuntu 11.10 64 bits on a Gigabyte H67M-D2 with an Intel i5-2400 CPU @ 3.10GHz.

Here is a portion of a recurrent error dumped in my syslog and ttys :

```
Jan 22 21:50:42 desktopi5 kernel: [  994.207005] ata5.00: status: { DRDY }
Jan 22 21:50:42 desktopi5 kernel: [  994.207010] ata5: hard resetting link
Jan 22 21:50:42 desktopi5 kernel: [  994.696021] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 22 21:50:42 desktopi5 kernel: [  994.698512] ata5.00: configured for UDMA/33
Jan 22 21:50:42 desktopi5 kernel: [  994.712006] ata5: EH complete
Jan 22 21:50:42 desktopi5 kernel: [  994.713173] ata5.00: exception Emask 0x50 SAct 0x3 SErr 0x480900 action 0x6 frozen
Jan 22 21:50:42 desktopi5 kernel: [  994.713177] ata5.00: irq_stat 0x08000000, interface fatal error
Jan 22 21:50:42 desktopi5 kernel: [  994.713181] ata5: SError: { UnrecovData HostInt 10B8B Handshk }
Jan 22 21:50:42 desktopi5 kernel: [  994.713185] ata5.00: failed command: READ FPDMA QUEUED
Jan 22 21:50:42 desktopi5 kernel: [  994.713191] ata5.00: cmd 60/20:00:d8:09:79/00:00:5d:00:00/40 tag 0 ncq 16384 in
Jan 22 21:50:42 desktopi5 kernel: [  994.713193]          res 40/00:08:00:1c:3d/00:00:0d:00:00/40 Emask 0x50 (ATA bus error)
```Whole error cap. [http://pastebin.com/EAtFApPz](http://pastebin.com/EAtFApPz)

do you know what it means?

---

### Post by searchfgold6789 on 2012-01-22
> ```
Jan 22 21:38:09 desktopi5 kernel: [  241.823952] ata5.00: failed command: WRITE FPDMA QUEUED
```It seems that the disk is not getting enough power or is damaged, or the cable is bad. But most likely it's damaged.

---

### Post by granjerox on 2012-01-23
could it be a bus problem or a problem with sata controler driver? I doubt it was that the disk is damaged because  i've just bought it. And I bought the new one because of this kind of problems.

---

### Post by searchfgold6789 on 2012-01-24
Yes, it could be either of those. :-k

---

