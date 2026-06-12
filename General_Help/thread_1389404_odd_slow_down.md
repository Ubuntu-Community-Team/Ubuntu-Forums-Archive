---
title: "odd slow down"
date: 2010-01-24
forum: General Help
---

### Post by eidoslinux on 2010-01-24
my system is acting really odd for a couple of days now. i am using Ubuntu 9.10 64bit edition Gnome and kernel 2.6.31-17-generic w/ 4gigs of ram and well over 150gigs of hd space. does anyone have a clue to my problem. otherwise i am going to have to reinstall and that would suck!

The error in kern.log
```
Jan 24 11:58:22 Alice kernel: [97623.437661] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 24 11:58:22 Alice kernel: [97623.437668] ata5.00: BMDMA stat 0x64
Jan 24 11:58:22 Alice kernel: [97623.437679] ata5.00: cmd c8/00:08:9a:ad:00/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 24 11:58:22 Alice kernel: [97623.437681]          res 51/40:00:9d:ad:00/00:00:00:00:00/e0 Emask 0x9 (media error)
Jan 24 11:58:22 Alice kernel: [97623.437686] ata5.00: status: { DRDY ERR }
Jan 24 11:58:22 Alice kernel: [97623.437689] ata5.00: error: { UNC }
Jan 24 11:58:22 Alice kernel: [97623.493209] ata5.00: configured for UDMA/100
Jan 24 11:58:22 Alice kernel: [97623.532988] ata5.01: configured for UDMA/66
Jan 24 11:58:22 Alice kernel: [97623.533006] ata5: EH complete
```

then message log
```
Jan 24 11:57:26 Alice kernel: [97567.343186] ata5.00: configured for UDMA/100
Jan 24 11:57:26 Alice kernel: [97567.383037] ata5.01: configured for UDMA/66
Jan 24 11:57:26 Alice kernel: [97567.383055] ata5: EH complete
Jan 24 11:57:27 Alice kernel: [97568.763226] ata5.00: configured for UDMA/100
Jan 24 11:57:27 Alice kernel: [97568.802999] ata5.01: configured for UDMA/66
Jan 24 11:57:27 Alice kernel: [97568.803017] ata5: EH complete
Jan 24 11:57:29 Alice kernel: [97570.204326] ata5.00: configured for UDMA/100
Jan 24 11:57:29 Alice kernel: [97570.242940] ata5.01: configured for UDMA/66
Jan 24 11:57:29 Alice kernel: [97570.242954] ata5: EH complete
Jan 24 11:57:30 Alice kernel: [97571.643195] ata5.00: configured for UDMA/100
Jan 24 11:57:30 Alice kernel: [97571.682987] ata5.01: configured for UDMA/66
Jan 24 11:57:30 Alice kernel: [97571.683008] ata5: EH complete
Jan 24 11:57:32 Alice kernel: [97573.083167] ata5.00: configured for UDMA/100
Jan 24 11:57:32 Alice kernel: [97573.122998] ata5.01: configured for UDMA/66
Jan 24 11:57:32 Alice kernel: [97573.123019] ata5: EH complete
Jan 24 11:57:33 Alice kernel: [97574.523137] ata5.00: configured for UDMA/100
Jan 24 11:57:33 Alice kernel: [97574.563005] ata5.01: configured for UDMA/66
Jan 24 11:57:33 Alice kernel: [97574.563027] sd 4:0:0:0: [sdc] Unhandled sense code
Jan 24 11:57:33 Alice kernel: [97574.563030] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 24 11:57:33 Alice kernel: [97574.563036] sd 4:0:0:0: [sdc] Sense Key : Medium Error [current] [descriptor]
Jan 24 11:57:33 Alice kernel: [97574.563042] Descriptor sense data with sense descriptors (in hex):
Jan 24 11:57:33 Alice kernel: [97574.563045]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 24 11:57:33 Alice kernel: [97574.563060]         00 00 ad 9d 
Jan 24 11:57:33 Alice kernel: [97574.563065] sd 4:0:0:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
```

---

