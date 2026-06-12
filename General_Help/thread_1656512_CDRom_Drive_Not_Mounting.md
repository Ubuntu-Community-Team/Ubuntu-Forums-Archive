---
title: "CDRom Drive Not Mounting"
date: 2010-12-31
forum: General Help
---

### Post by kwestjones on 2010-12-31
I did a new install of Kubuntu 10.10 on a Gateway MX6734 Laptop.  Everything appeared to be running well.  I should say, everything is running well but when I went to install Vista into Virtual Box I noticed that the CD Rom wasn't mounted.  I rebooted the laptop and got this from dmesg (grepped ata out):

[    0.000000] Memory: 1004872k/1038848k available (4931k kernel code, 33524k reserved, 2333k data, 688k init, 129544k highmem)
[    0.000000]       .data : 0xc05d0ebe - 0xc08184e8   (2333 kB)
[    0.192169] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.211791] libata version 3.00 loaded.
[    0.314597] ata_piix 0000:00:1f.1: version 2.13
[    0.314637] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.314700] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.315187] scsi0 : ata_piix
[    0.320936] scsi1 : ata_piix
[    0.321876] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.321882] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.341359] ata2: port disabled. ignoring.
[    0.521821] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PG02, max UDMA/33
[    0.537608] ata1.00: configured for UDMA/33
[    0.699525] Write protecting the kernel read-only data: 1980k
[    0.951095] ata3: SATA max UDMA/133 abar m1024@0xd4444400 port 0xd4444500 irq 41
[    0.951098] ata4: DUMMY
[    0.951104] ata5: SATA max UDMA/133 abar m1024@0xd4444400 port 0xd4444600 irq 41
[    0.951107] ata6: DUMMY
[    1.269123] ata5: SATA link down (SStatus 0 SControl 300)
[    1.548110] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.549020] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.580717] ata3.00: ATA-7: WDC WD1600BEVS-22RST0, 04.01G04, max UDMA/133
[    1.580721] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.581706] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.581997] ata3.00: configured for UDMA/133
[    1.980571] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  256.032174] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  256.032186] ata1.00: ST_FIRST: !(DRQ|ERR|DF)
[  256.032227] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  256.032284] ata1: soft resetting link
[  256.197519] ata1.00: model number mismatch 'HL-DT-ST DVDRAM GSA-T10N' != 'HL-DTmST DVDRAM`GSAmTq0N ` ` ` ` ` ` ` `'
[  256.197530] ata1.00: revalidation failed (errno=-19)
[  261.188145] ata1: soft resetting link
[  261.352489] ata1.00: model number mismatch 'HL-DT-ST DVDRAM GSA-T10N' != 'HL-DTmST DVDRAM`GSAmTq0N ` ` ` ` ` ` ` `'
[  261.352501] ata1.00: revalidation failed (errno=-19)
[  261.352510] ata1.00: disabled
[  261.352549] ata1: EH complete
[  261.352573] ata1.00: detaching (SCSI 0:0:0:0)

I am fairly new to ubuntu so I am not really sure where I would find where the 'module number' is misassigned.

Any help would be greatly appreciated.

Thanks

---

