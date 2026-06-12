---
title: "Periods of unresponsiveness"
date: 2009-11-26
forum: General Help
---

### Post by keithclark on 2009-11-26
My system seems to become unresponsive every about half hour and the
Load goes through the roof.  CPU usage does not seem to be high, nor
network usage during this period.

I looked at my syslog for that time period and I see the following block
of entries over and over again:

Nov 25 11:28:57 bookworm-acerdesktop kernel: [ 9440.533198] ata1.00:
exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
Nov 25 11:28:57 bookworm-acerdesktop kernel: [ 9440.533208] ata1.00:
irq_stat 0x40000008
Nov 25 11:28:57 bookworm-acerdesktop kernel: [ 9440.533226] ata1.00: cmd
60/f8:08:89:22:8b/00:00:1b:00:00/40 tag 1 ncq 126976 in
Nov 25 11:28:57 bookworm-acerdesktop kernel: [ 9440.533230]          res
41/40:00:22:23:8b/e7:00:1b:00:00/40 Emask 0x409 (media error) <F>
Nov 25 11:28:57 bookworm-acerdesktop kernel: [ 9440.533260] ata1.00:
status: { DRDY ERR }
Nov 25 11:28:57 bookworm-acerdesktop kernel: [ 9440.533264] ata1.00:
error: { UNC }
Nov 25 11:28:57 bookworm-acerdesktop kernel: [ 9440.534164] ata1.00:
SB600 AHCI: limiting to 255 sectors per cmd
Nov 25 11:28:57 bookworm-acerdesktop kernel: [ 9440.535146] ata1.00:
SB600 AHCI: limiting to 255 sectors per cmd
Nov 25 11:28:57 bookworm-acerdesktop kernel: [ 9440.535152] ata1.00:
configured for UDMA/133
Nov 25 11:28:57 bookworm-acerdesktop kernel: [ 9440.535171] ata1: EH
complete

Is this evidence of a drive error?  It seems to have begun after a power
failure and only happens to one user, the one who was logged in at the
time of the power failure.  The other user does not experience this same
issue.

Thanks,

Keith

---

### Post by dcstar on 2009-11-27
> **keithclark said:**
> My system seems to become unresponsive every about half hour and the
Load goes through the roof.  CPU usage does not seem to be high, nor
network usage during this period.
.........
Is this evidence of a drive error?  It seems to have begun after a power
failure and only happens to one user, the one who was logged in at the
time of the power failure.  The other user does not experience this same
issue.


Quite possibly part of the hard disk with that user's files on it is bad.

Install the **smartmontools** package and run some diagnostics.

---

### Post by keithclark on 2009-11-27
> **dcstar said:**
> Quite possibly part of the hard disk with that user's files on it is bad.

Install the **smartmontools** package and run some diagnostics.

Running System>Administration>Disk Utility shows that there is one bad sector.  It also reports a wrong disk size so I'm assuming that the sector count is also bad.

Disk Utility will not let me fix the drive though.  Not sure where to go from here.

Keith

---

### Post by keithclark on 2009-11-29
> **keithclark said:**
> Running System>Administration>Disk Utility shows that there is one bad sector.  It also reports a wrong disk size so I'm assuming that the sector count is also bad.

Disk Utility will not let me fix the drive though.  Not sure where to go from here.

Keith

Ok, I initiated the disk check upon reboot and still no errors are reported.  The drive is still reporting the wrong size and my system locks up for 5 minutes every half hour.

Keith

---

### Post by keithclark on 2009-12-09
Here is the complete listing of syslog when there is a period of unresponsiveness every half hour.

Dec  9 09:35:32 bookworm-acerdesktop kernel: [236267.848080] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236267.856044] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236267.856048] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236267.856067] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236271.356680] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236271.358244] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236271.358249] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236271.358268] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236274.449238] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236274.459904] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236274.459909] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236274.459928] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236277.556045] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236277.568043] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236277.568047] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236277.568066] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236280.811011] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236280.811987] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236280.811994] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236280.812027] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.053418] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.054396] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.054402] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.054433] sd 0:0:0:0: [sda] Unhandled sense code
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.054437] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.054445] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.054454] Descriptor sense data with sense descriptors (in hex):
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.054459]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.054477]         1b 8b 23 22 
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.054485] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236284.054520] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236287.294887] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236287.297649] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236287.297656] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236287.297679] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236290.377374] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236290.378760] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236290.378767] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236290.378788] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236293.643082] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236293.644323] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236293.644329] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236293.644356] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236297.053547] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236297.055462] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236297.055469] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236297.055491] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236300.301945] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236300.302934] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236300.302940] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236300.302963] ata1: EH complete
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.543451] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.545803] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.545810] ata1.00: configured for UDMA/133
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.545834] sd 0:0:0:0: [sda] Unhandled sense code
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.545839] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.545847] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.545857] Descriptor sense data with sense descriptors (in hex):
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.545862]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.545878]         1b 8b 23 22 
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.545885] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Dec  9 09:35:32 bookworm-acerdesktop kernel: [236303.545928] ata1: EH complete

---

