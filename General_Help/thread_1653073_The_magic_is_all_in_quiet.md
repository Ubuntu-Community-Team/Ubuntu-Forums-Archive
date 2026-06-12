---
title: "The magic is all in quiet"
date: 2010-12-26
forum: General Help
---

### Post by gawadelnil2002 on 2010-12-26
Hey everybody ,I had some issues after installing ubuntu 10.10 and 10.04 now Im holding on ubuntu 10.10 stable as U know it was released 10/10/2010 :) perfect 10.
The issue is a delay in boot process because of hard disk error:
```
[   31.840030] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x6 frozen
[   31.840038] ata1.00: failed command: READ FPDMA QUEUED
[   31.840046] ata1.00: cmd 60/01:00:3f:19:c0/00:00:01:00:00/40 tag 0 ncq 512 in
[   31.840051] ata1.00: status: { DRDY }
[   31.840055] ata1.00: failed command: READ FPDMA QUEUED
[   31.840061] ata1.00: cmd 60/08:08:24:1a:c0/00:00:01:00:00/40 tag 1 ncq 4096 in
[   31.840066] ata1.00: status: { DRDY }
[   31.840073] ata1: hard resetting link
```

Googled alot, I saw many threads about that, most of them ends with agreement that it was cable problem or bad hard disk or bad power supply ,so I said to myself it time to change hard disk now :) god give me the money.
For some reason I took my hard disk with me when I was going to buy new one, and I made people check it there before I buy new one ,they said it is very ok it may be driver issue.
on web I saw a bug report said that the solution is to disable ncq during boot through a boot parameter. I used it It didn't work ,I was on my own in this 
Started debugging with removing quiet from grub and update-grub then restart to see the hidden pre-boot messages ,I found no error and my machine was super fast I did not except that 
that dmesg message without "quiet"
```
mohammed@Mohammed:~$ cat /var/log/dmesg.0 | grep ata
[    0.000000]  BIOS-e820: 000000002ff90000 - 000000002ff9e000 (ACPI data)
[    0.000000]  modified: 000000002ff90000 - 000000002ff9e000 (ACPI data)
[    0.000000] Memory: 758892k/785984k available (4931k kernel code, 26640k reserved, 2333k data, 688k init, 0k highmem)
[    0.000000]       .data : 0xc05d0ebe - 0xc08184e8   (2333 kB)
[    0.127138] libata version 3.00 loaded.
[    0.435374] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.436371] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.484273] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.484291] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    1.635386] Write protecting the kernel read-only data: 1980k
[    2.142000] ata1: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 23
[    2.154582] ata2: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c180 irq 23
[    2.167152] ata3: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c200 irq 23
[    2.179552] ata4: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c280 irq 23
[    2.508016] ata3: SATA link down (SStatus 0 SControl 300)
[    2.519999] ata2: SATA link down (SStatus 0 SControl 300)
[    2.531602] ata4: SATA link down (SStatus 0 SControl 300)
[    2.912022] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.925682] ata1.00: ATA-7: Maxtor 6V160E0, VA111630, max UDMA/133
[    2.936934] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.951268] ata1.00: configured for UDMA/133
[    4.181789] EXT3-fs (sda1): mounted filesystem with ordered data mode
[   15.107850] pata_amd 0000:00:08.0: version 0.4.1
[   15.107911] pata_amd 0000:00:08.0: setting latency timer to 64
[   15.136472] scsi4 : pata_amd
[   15.145429] scsi5 : pata_amd
[   15.147879] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   15.147884] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   15.332328] ata5.00: ATAPI: LG (OEM)CD-ROM CRD-8521B, 2.00, max MWDMA2
[   15.332377] ata5.01: ATAPI: TSSTcorpCD-R/RW SH-R522C, TS05, max UDMA/33
[   15.332414] ata5: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc00000) ACPI=0x39f (120:60:0x14)
[   15.332420] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc00000) ACPI=0x701f (120:60:0x14)
[   15.340286] ata5.00: configured for MWDMA2
[   15.348279] ata5.01: configured for UDMA/33
[   15.362647] ata6: port disabled. ignoring.
```

then I added quiet in grub before I boot and bingo the error appeared and the delay come back again
```
mohammed@Mohammed:~$ cat /var/log/dmesg | grep ata
[    0.000000]  BIOS-e820: 000000002ff90000 - 000000002ff9e000 (ACPI data)
[    0.000000]  modified: 000000002ff90000 - 000000002ff9e000 (ACPI data)
[    0.000000] Memory: 758892k/785984k available (4931k kernel code, 26640k reserved, 2333k data, 688k init, 0k highmem)
[    0.000000]       .data : 0xc05d0ebe - 0xc08184e8   (2333 kB)
[    0.126906] libata version 3.00 loaded.
[    0.426933] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.427494] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.427516] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.427527] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.848684] Write protecting the kernel read-only data: 1980k
[    1.187550] ata1: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c100 irq 23
[    1.187554] ata2: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c180 irq 23
[    1.187558] ata3: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c200 irq 23
[    1.187561] ata4: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c280 irq 23
[    1.504024] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.504044] ata2: SATA link down (SStatus 0 SControl 300)
[    1.506441] ata1.00: ATA-7: Maxtor 6V160E0, VA111630, max UDMA/133
[    1.506445] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.508014] ata4: SATA link down (SStatus 0 SControl 300)
[    1.508034] ata3: SATA link down (SStatus 0 SControl 300)
[    1.509675] ata1.00: configured for UDMA/133
[COLOR=Blue][   31.840030] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x6 frozen
[   31.840038] ata1.00: failed command: READ FPDMA QUEUED
[   31.840046] ata1.00: cmd 60/01:00:3f:19:c0/00:00:01:00:00/40 tag 0 ncq 512 in
[   31.840051] ata1.00: status: { DRDY }
[   31.840055] ata1.00: failed command: READ FPDMA QUEUED
[   31.840061] ata1.00: cmd 60/08:08:24:1a:c0/00:00:01:00:00/40 tag 1 ncq 4096 in
[   31.840066] ata1.00: status: { DRDY }
[   31.840073] ata1: hard resetting link[/COLOR]
[   32.160016] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   32.165405] ata1.00: configured for UDMA/133
[   32.165412] ata1.00: device reported invalid CHS sector 0
[   32.165422] ata1: EH complete
[   33.235430] EXT3-fs (sda1): mounted filesystem with ordered data mode
[   44.373490] pata_amd 0000:00:08.0: version 0.4.1
[   44.373546] pata_amd 0000:00:08.0: setting latency timer to 64
[   44.384128] scsi4 : pata_amd
[   44.399069] scsi5 : pata_amd
[   44.401252] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   44.401256] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   44.583324] ata5.00: ATAPI: LG (OEM)CD-ROM CRD-8521B, 2.00, max MWDMA2
[   44.583373] ata5.01: ATAPI: TSSTcorpCD-R/RW SH-R522C, TS05, max UDMA/33
[   44.583411] ata5: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc00000) ACPI=0x39f (120:60:0x14)
[   44.583417] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc00000) ACPI=0x701f (120:60:0x14)
[   45.586378] ata5.00: configured for MWDMA2
[   45.838677] ata5.01: configured for UDMA/33
[   45.854705] ata6: port disabled. ignoring.
```

I don't what is this what is the magic in quiet but I can say this is regenerated every time I repeat the previous procedure ,and I'm sure too that the delay in boot happens at this error ,I saw  that by my eyes when I removed splash from grub too I saw it hangs at this text and give that error 
I'm going to report a bug but before I do that I wanted opinions and may a solution . or some one tell me what is this to add that in the bug report. 

Thanks in advance and please  all experienced people try to help me

---

### Post by dcstar on 2010-12-26
> **gawadelnil2002 said:**
> 
..........
Googled alot, I saw many threads about that, most of them ends with agreement that it was cable problem or bad hard disk or bad power supply ,so I said to myself it time to change hard disk now :) god give me the money.
For some reason I took my hard disk with me when I was going to buy new one, and I made people check it there before I buy new one ,**they said it is very ok** it may be driver issue.
.........
Thanks in advance and please  all experienced people try to help me

Unreliable hard disks on the verge of failure may well work **sometimes**. Replace it.

---

