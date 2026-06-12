---
title: "ata error messages"
date: 2010-08-06
forum: General Help
---

### Post by lupus73 on 2010-08-06
I have just installed ubuntu server on an old desktop, and everything seems to be working ok, but I keep getting some strange error messages in the startup. Lots of messages like shown below is displayed on the screen. Unfortunately my Linux competence has been neglected so apologize if this is a really dumb question...

Logfile shows a lot of this...

[  109.326144] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  109.326329] ata1.01: BMDMA stat 0x64
[  109.326436] ata1.01: failed command: READ DMA EXT
[  109.326572] ata1.01: cmd 25/00:08:f0:73:15/00:00:13:00:00/f0 tag 0 dma 4096 in
[  109.326574]          res 51/40:00:f5:73:15/40:00:13:00:00/f0 Emask 0x9 (media error)
[  109.326990] ata1.01: status: { DRDY ERR }
[  109.327102] ata1.01: error: { UNC }
[  109.340311] ata1.00: configured for UDMA/100
[  109.356400] ata1.01: configured for UDMA/100
[  109.356413] ata1: EH complete
[  110.439773] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  110.439955] ata1.01: BMDMA stat 0x64
[  110.440079] ata1.01: failed command: READ DMA EXT
[  110.440215] ata1.01: cmd 25/00:08:f0:73:15/00:00:13:00:00/f0 tag 0 dma 4096 in
[  110.440217]          res 51/40:00:f5:73:15/40:00:13:00:00/f0 Emask 0x9 (media error)
[  110.440631] ata1.01: status: { DRDY ERR }
[  110.440742] ata1.01: error: { UNC }

\\lupus73

---

### Post by gwilson on 2010-09-06
I am having a very similar problem with a standard desktop install of 10.04 every time I boot. This started about the same time an error reading "Power Manager not responding" started showing up.

My error messages appear to be identical to yours.

---

