---
title: "Server is crashing"
date: 2011-07-31
forum: General Help
---

### Post by rideon88 on 2011-07-31
My ubuntu server running 10.10 (which has been rock solid for over a year) is now freezing regularly. I have logwatch setup and after I hard reboot it I get these errors in the kernel section.

Looks like the logs reference ata which sounds like my hard disk. I am running a standard raid 1 using the mobo's raid controller.  

Where should I begin to debug this?


 --------------------- Kernel Begin ------------------------


 1 Time(s):          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
 1 Time(s): ata5.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
 1 Time(s): ata5.00: configured for UDMA/100
 1 Time(s): ata5.00: device reported invalid CHS sector 0
 1 Time(s): ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
 1 Time(s): ata5.00: failed command: FLUSH CACHE EXT
 1 Time(s): ata5.00: retrying FLUSH 0xea Emask 0x4
 1 Time(s): ata5.00: status: { DRDY }
 1 Time(s): ata5: EH complete
 1 Time(s): ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
 3 Time(s): ata5: hard resetting link
 2 Time(s): ata5: softreset failed (timeout)

 ---------------------- Kernel End -------------------------

---

### Post by Gyokuro on 2011-07-31
Check your PSU, SATA cables - could be a problem with your onboard raid chip (what's kind of raid chip (intel,...)?)

---

