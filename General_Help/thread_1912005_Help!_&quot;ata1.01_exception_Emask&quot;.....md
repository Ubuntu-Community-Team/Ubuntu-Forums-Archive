---
title: "Help! &quot;ata1.01: exception Emask&quot;?...."
date: 2012-01-19
forum: General Help
---

### Post by VcDeveloper on 2012-01-19
My system crashed twice and I wasn't able to find the problem, but today I saw my CD/DVD Rom lite blinking and check the syslog and got this:

```
Jan 19 16:38:06 anointed-server kernel: [1757901.010337] ata1.01: exception Emask 0x10 SAct 0x0 SErr 0x4050002 action 0x0
Jan 19 16:38:06 anointed-server kernel: [1757901.010346] ata1.01: SError: { RecovComm PHYRdyChg CommWake DevExch }
Jan 19 16:38:06 anointed-server kernel: [1757901.010351] sr 0:0:1:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Jan 19 16:38:06 anointed-server kernel: [1757901.010369] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jan 19 16:38:06 anointed-server kernel: [1757901.010371]          res 00/01:01:01:14:eb/00:00:00:00:00/10 Emask 0x12 (ATA bus error)
Jan 19 16:38:06 anointed-server kernel: [1757901.010383] ata1.00: hard resetting link
Jan 19 16:38:06 anointed-server kernel: [1757901.760023] ata1.01: hard resetting link
Jan 19 16:38:07 anointed-server kernel: [1757902.670076] ata1.00: SATA link down (SStatus 0 SControl 300)
Jan 19 16:38:07 anointed-server kernel: [1757902.670092] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 19 16:38:07 anointed-server kernel: [1757902.740231] ata1.01: configured for UDMA/100
Jan 19 16:38:07 anointed-server kernel: [1757902.748778] ata1: EH complete

```

Can anyone explain what this mean?

---

