---
title: "had some error msg come up about ata while starting up, how do i find out what it was"
date: 2010-12-06
forum: General Help
---

### Post by fuzzylogic25 on 2010-12-06
I hibernated my computer, then turned it back on. It came up with some error msg that looked like this:

2035.2350 ata2 ...........errno = 16

actually, the numbers are wrong and the dots represent some other text i couldnt get. also, i wasnt sure what the error number was. is there any way i can find out what it was? I thought maybe ubuntu would have logged it down?

---

### Post by hawthornso23 on 2010-12-06
in a terminal

```
dmesg | grep ata
```

'dmesg' prints system messages. 
'|' is a pipe 
'grep ata' searchs for all lines containing `ata' and prints only those.

---

### Post by fuzzylogic25 on 2010-12-06
ok i did that and got this:

========================================================

[    0.000000]  BIOS-e820: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
[    0.000000]  modified: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] Memory: 4049688k/4653056k available (4835k kernel code, 76384k reserved, 2218k data, 672k init, 3216264k highmem)
[    0.000000]       .data : 0xc05b8cef - 0xc07e3828   (2218 kB)
[    0.211391] libata version 3.00 loaded.
[    0.284362] ata_piix 0000:00:1f.2: version 2.13
[    0.284379] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.284385] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.439788] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.439895] scsi0 : ata_piix
[    0.440013] scsi1 : ata_piix
[    0.440756] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.440762] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.440794] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.440800] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.440842] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.440919] scsi2 : ata_piix
[    0.440977] scsi3 : ata_piix
[    0.441571] ata3: SATA max UDMA/133 cmd 0xd800 ctl 0xdc00 bmdma 0xe800 irq 19
[    0.441575] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xe400 bmdma 0xe808 irq 19
[    0.441652] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    0.441658] pata_acpi 0000:03:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.441690] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.441705] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.779031] ata4: SATA link down (SStatus 0 SControl 300)
[    0.933332] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.941724] ata3.00: ATA-8: Hitachi HDS722020ALA330, JKAOA3EA, max UDMA/133
[    0.941728] ata3.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.957859] ata3.00: configured for UDMA/133
[    1.236207] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.236220] ata1.01: SATA link down (SStatus 4 SControl 300)
[    1.244081] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.244093] ata2.01: SATA link down (SStatus 4 SControl 300)
[    1.253009] ata2.00: ATA-8: WDC WD20EARS-00MVWB0, 50.0AB50, max UDMA/133
[    1.253013] ata2.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.261068] ata2.00: configured for UDMA/133
[    1.268202] ata1.00: HPA unlocked: 586070255 -> 586072368, native 586072368
[    1.268207] ata1.00: ATA-8: WDC WD3000HLFS-01G6U1, 04.04V02, max UDMA/133
[    1.268211] ata1.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.285464] ata1.00: configured for UDMA/133
[    1.344702] Write protecting the kernel read-only data: 1884k
[    1.486884] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.486919] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.493589] scsi4 : pata_jmicron
[    1.497137] scsi5 : pata_jmicron
[    1.497871] ata5: PATA max UDMA/100 cmd 0x9000 ctl 0x9400 bmdma 0xa000 irq 16
[    1.497875] ata6: PATA max UDMA/100 cmd 0x9800 ctl 0x9c00 bmdma 0xa008 irq 16
[    1.512484] ata7: SATA max UDMA/133 abar m8192@0xf9000000 port 0xf9000100 irq 19
[    1.512488] ata8: SATA max UDMA/133 abar m8192@0xf9000000 port 0xf9000180 irq 19
[    1.664642] ata5.00: ATAPI: PIONEER DVD-RW  DVR-111D, 1.29, max UDMA/66
[    1.681111] ata5.00: configured for UDMA/66
[    1.705668] EXT3-fs: mounted filesystem with ordered data mode.
[    1.836072] ata7: SATA link down (SStatus 0 SControl 300)
[    1.836105] ata8: SATA link down (SStatus 0 SControl 300)
[   38.943613] ata3.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[   38.943617] ata3.00: BMDMA stat 0x26
[   38.943621] ata3: SError: { UnrecovData HostInt 10B8B BadCRC }
[   38.943625] ata3.00: failed command: READ DMA EXT
[   38.943631] ata3.00: cmd 25/00:00:67:ec:46/00:01:74:00:00/e0 tag 0 dma 131072 in
[   38.943636] ata3.00: status: { DRDY ERR }
[   38.943638] ata3.00: error: { ICRC ABRT }
[   38.943646] ata3: hard resetting link
[   39.416555] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   39.440914] ata3.00: configured for UDMA/133
[   39.440928] ata3: EH complete
[   39.645883] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x280100 action 0x6
[   39.645888] ata3.00: BMDMA stat 0x26
[   39.645891] ata3: SError: { UnrecovData 10B8B BadCRC }
[   39.645895] ata3.00: failed command: READ DMA EXT
[   39.645901] ata3.00: cmd 25/00:00:17:d9:46/00:01:74:00:00/e0 tag 0 dma 131072 in
[   39.645906] ata3.00: status: { DRDY ERR }
[   39.645908] ata3.00: error: { ICRC ABRT }
[   39.645916] ata3: hard resetting link
[   40.120605] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   40.144446] ata3.00: configured for UDMA/133
[   40.144461] ata3: EH complete
[   40.165387] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x280100 action 0x6
[   40.165392] ata3.00: BMDMA stat 0x26
[   40.165396] ata3: SError: { UnrecovData 10B8B BadCRC }
[   40.165401] ata3.00: failed command: READ DMA EXT
[   40.165407] ata3.00: cmd 25/00:00:bf:e2:46/00:01:74:00:00/e0 tag 0 dma 131072 in
[   40.165413] ata3.00: status: { DRDY ERR }
[   40.165416] ata3.00: error: { ICRC ABRT }
[   40.165424] ata3: hard resetting link
[   40.640576] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   40.664440] ata3.00: configured for UDMA/133
[   40.664454] ata3: EH complete
[   40.854609] ata3: limiting SATA link speed to 1.5 Gbps
[   40.854615] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x280100 action 0x6
[   40.854620] ata3.00: BMDMA stat 0x26
[   40.854624] ata3: SError: { UnrecovData 10B8B BadCRC }
[   40.854628] ata3.00: failed command: READ DMA EXT
[   40.854636] ata3.00: cmd 25/00:a8:8f:7c:47/00:00:74:00:00/e0 tag 0 dma 86016 in
[   40.854641] ata3.00: status: { DRDY ERR }
[   40.854644] ata3.00: error: { ICRC ABRT }
[   40.854652] ata3: hard resetting link
[   41.328073] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   41.353002] ata3.00: configured for UDMA/133
[   41.353018] ata3: EH complete
[   46.377554] EXT4-fs (sdc1): mounted filesystem with ordered data mode

=================================================================

but i actually restarted the computer first then did this. and when i restarted the computer the error msg did not come up. so is it possible that this is a log of the recent start up process only? or does it include everything?

---

### Post by hawthornso23 on 2010-12-07
ICRC error = Interface CRC error during Ultra DMA transfer - often  either a bad cable or power problem, though possibly an incorrect Ultra  DMA mode setting by the driver.

So what does this mean? The place to start is probably checking the cables on your hard drives are connected properly. Then maybe have a look at voltage on your PSU.

---

