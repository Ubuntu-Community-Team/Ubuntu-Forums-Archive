---
title: "Optical drive requires special SATA configuration in BIOS... any workaround?"
date: 2011-07-19
forum: General Help
---

### Post by stretch44 on 2011-07-19
Hi there,  

I've recently installed an internal optical drive (Blu-Ray RW: LG WH10LS30) into my dual boot system.  The Windows partition had no trouble with this.  However, ubuntu began taking ~30 extra seconds to boot.  Once ubuntu finally gets running, the drive is not detected at all.  dmesg showed the following:  

```
$ sudo dmesg | grep -i 'ata2'
[    1.430315] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf098 irq 15
[    2.777449] ata2.01: failed to resume link (SControl 0)
[    2.933509] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.933521] ata2.01: SATA link down (SStatus 4 SControl 0)
[    2.933531] ata2.01: link offline, clearing class 3 to NONE
[    2.957608] ata2.00: ATAPI: HL-DT-ST BD-RE  WH10LS30, 1.00, max UDMA/133
[    2.989610] ata2.00: configured for UDMA/133
[    7.989314] ata2.00: qc timeout (cmd 0xa0)
[    7.989319] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[    9.337296] ata2.01: failed to resume link (SControl 0)
[    9.493331] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.493343] ata2.01: SATA link down (SStatus 4 SControl 0)
[    9.493352] ata2.01: link offline, clearing class 3 to NONE
[    9.549445] ata2.00: configured for UDMA/133
[   14.549164] ata2.00: qc timeout (cmd 0xa0)
[   14.549165] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[   14.549168] ata2.00: limiting SATA link speed to 1.5 Gbps
[   14.549169] ata2.00: limiting speed to UDMA/133:PIO3
[   15.897104] ata2.01: failed to resume link (SControl 0)
[   16.053166] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   16.053178] ata2.01: SATA link down (SStatus 4 SControl 0)
[   16.053188] ata2.01: link offline, clearing class 3 to NONE
[   16.109274] ata2.00: configured for UDMA/133
[   21.108963] ata2.00: qc timeout (cmd 0xa0)
[   21.108965] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[   21.108966] ata2.00: disabled
[   21.108976] ata2.00: hard resetting link
[   21.428990] ata2.01: hard resetting link
[   22.456953] ata2.01: failed to resume link (SControl 0)
[   22.613005] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   22.613017] ata2.01: SATA link down (SStatus 4 SControl 0)
[   22.613026] ata2.01: link offline, clearing class 3 to NONE
[   22.613028] ata2: EH complete

```

Further investigation revealed that changing my BIOS settings for SATA from IDE to AHCI fixed this problem entirely.  The ubuntu partition boots fast again, the drive is working.  Except, this causes the Windows partition to fail completely.  

I'm wondering, what is the best way to fix this?  Hopefully without a complete reinstall.  Is there a GRUB command that could apply AHCI to only the optical drive during ubuntu boot?  

Thanks!

---

### Post by 2F4U on 2011-07-19
Windows is known to have a problem when the setting is changed from IDE to AHCI, at least Windows XP. I am not sure about Windows 7.

---

### Post by dcstar on 2011-07-20
> **stretch44 said:**
> 
........
Further investigation revealed that changing my BIOS settings for SATA from IDE to **AHCI fixed this problem entirely**.  The ubuntu partition boots fast again, the drive is working.  **Except, this causes the Windows partition to fail completely**.  

I'm wondering, what is the best way to fix this?  Hopefully without a complete reinstall.  Is there a GRUB command that could apply AHCI to only the optical drive during ubuntu boot?  

Thanks!

Fix Windows and use AHCI:

[http://www.sevenforums.com/tutorials/61869-ahci-enable-windows-7-vista.html?ltr=A](http://www.sevenforums.com/tutorials/61869-ahci-enable-windows-7-vista.html?ltr=A)

---

