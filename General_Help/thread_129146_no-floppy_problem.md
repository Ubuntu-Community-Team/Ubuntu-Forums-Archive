---
title: "no-floppy problem"
date: 2006-02-13
forum: General Help
---

### Post by Vies1 on 2006-02-13
Hi everyone,

I'm currently having some problems with my laptop and kubuntu. I have DVD-rom on my laptop multibay but it wont be recoqnised correctly unless there's a disk inserted during boot.

In logs there is a text that says "cd-rom or floppy detected, asuming floppy" if there is no disk during boot. 
Is there way to disable that floppy asuming, since I very rarely have floppy-drive installed (let's say never)?

I can post clip of that log when I get home tonight

Thank you in advanced.

---

### Post by Vies1 on 2006-02-16
Here's some more info.

Laptop is old Omnibook 4150B. And in the bios, floppy is disabled (no present) and there is no option to enable/disable DVD-drive

During the boot,if there is no cd/DVD in the drive, the drive is detected, but assumed as floppy. Here's the log

```

Feb 15 20:15:36 localhost kernel: [4294673.840000] fb0: VGA16 VGA frame buffer device
Feb 15 20:15:36 localhost kernel: [4294675.141000] Capability LSM initialized
Feb 15 20:15:36 localhost kernel: [4294675.180000] NET: Registered protocol family 1
Feb 15 20:15:36 localhost kernel: [4294675.228000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb 15 20:15:36 localhost kernel: [4294675.228000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb 15 20:15:36 localhost kernel: [4294675.228000] ACPI: bus type ide registered
Feb 15 20:15:36 localhost kernel: [4294675.244000] PIIX4: IDE controller at PCI slot 0000:00:07.1
Feb 15 20:15:36 localhost kernel: [4294675.244000] PIIX4: chipset revision 1
Feb 15 20:15:36 localhost kernel: [4294675.244000] PIIX4: not 100%% native mode: will probe irqs later
Feb 15 20:15:36 localhost kernel: [4294675.244000]     ide0: BM-DMA at 0xfcf0-0xfcf7, BIOS settings: hda:DMA, hdb:pio
Feb 15 20:15:36 localhost kernel: [4294675.244000]     ide1: BM-DMA at 0xfcf8-0xfcff, BIOS settings: hdc:pio, hdd:pio
Feb 15 20:15:36 localhost kernel: [4294675.508000] hda: IBM-DJSA-220, ATA DISK drive
Feb 15 20:15:36 localhost kernel: [4294676.123000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb 15 20:15:36 localhost kernel: [4294676.489000] hdc: , ATAPI cdrom or floppy?, assuming FLOPPY drive
Feb 15 20:15:36 localhost kernel: [4294677.102000] ide1 at 0x170-0x177,0x376 on irq 15
Feb 15 20:15:36 localhost kernel: [4294679.169000] hda: max request size: 128KiB
Feb 15 20:15:36 localhost kernel: [4294679.213000] hda: 39070080 sectors (20003 MB) w/1874KiB Cache, CHS=41344/15/63, UDMA(33)
Feb 15 20:15:36 localhost kernel: [4294679.213000] hda: cache flushes not supported
Feb 15 20:15:36 localhost kernel: [4294679.213000]  /dev/ide/host0/bus0/target0/lun0: p1 p2
Feb 15 20:15:36 localhost kernel: [4294679.909000] Attempting manual resume
Feb 15 20:15:36 localhost kernel: [4294679.923000] swsusp: Suspend partition has wrong signature?
Feb 15 20:15:36 localhost kernel: [4294680.126000] usbcore: registered new driver usbfs
Feb 15 20:15:36 localhost kernel: [4294680.127000] usbcore: registered new driver hub
Feb 15 20:15:36 localhost kernel: [4294680.131000] USB Universal Host Controller Interface driver v2.2
Feb 15 20:15:36 localhost kernel: [4294680.131000] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
Feb 15 20:15:36 localhost kernel: [4294680.133000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
Feb 15 20:15:36 localhost kernel: [4294680.133000] PCI: setting IRQ 10 as level-triggered
Feb 15 20:15:36 localhost kernel: [4294680.133000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
```

And if there is CD/DVD, its detected correctly

```
Feb 15 22:15:32 localhost kernel: [4294672.269000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb 15 22:15:32 localhost kernel: [4294672.269000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb 15 22:15:32 localhost kernel: [4294672.269000] ACPI: bus type ide registered
Feb 15 22:15:32 localhost kernel: [4294672.286000] PIIX4: IDE controller at PCI slot 0000:00:07.1
Feb 15 22:15:32 localhost kernel: [4294672.286000] PIIX4: chipset revision 1
Feb 15 22:15:32 localhost kernel: [4294672.286000] PIIX4: not 100%% native mode: will probe irqs later
Feb 15 22:15:32 localhost kernel: [4294672.286000]     ide0: BM-DMA at 0xfcf0-0xfcf7, BIOS settings: hda:DMA, hdb:pio
Feb 15 22:15:32 localhost kernel: [4294672.286000]     ide1: BM-DMA at 0xfcf8-0xfcff, BIOS settings: hdc:DMA, hdd:pio
Feb 15 22:15:32 localhost kernel: [4294672.550000] hda: IBM-DJSA-220, ATA DISK drive
Feb 15 22:15:32 localhost kernel: [4294673.176000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb 15 22:15:32 localhost kernel: [4294673.542000] hdc: TOSHIBA DVD-ROM SD-C2302, ATAPI CD/DVD-ROM drive
Feb 15 22:15:32 localhost kernel: [4294674.156000] ide1 at 0x170-0x177,0x376 on irq 15
Feb 15 22:15:32 localhost kernel: [4294676.223000] hda: max request size: 128KiB
Feb 15 22:15:32 localhost kernel: [4294676.267000] hda: 39070080 sectors (20003 MB) w/1874KiB Cache, CHS=41344/15/63, UDMA(33)
Feb 15 22:15:32 localhost kernel: [4294676.267000] hda: cache flushes not supported
Feb 15 22:15:32 localhost kernel: [4294676.267000]  /dev/ide/host0/bus0/target0/lun0: p1 p2
Feb 15 22:15:32 localhost kernel: [4294676.322000] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache
Feb 15 22:15:32 localhost kernel: [4294676.322000] Uniform CD-ROM driver Revision: 3.20
Feb 15 22:15:32 localhost kernel: [4294677.188000] Attempting manual resume
Feb 15 22:15:32 localhost kernel: [4294677.191000] swsusp: Suspend partition has wrong signature?
Feb 15 22:15:32 localhost kernel: [4294677.394000] usbcore: registered new driver usbfs
Feb 15 22:15:32 localhost kernel: [4294677.394000] usbcore: registered new driver hub
Feb 15 22:15:32 localhost kernel: [4294677.399000] USB Universal Host Controller Interface driver v2.2
Feb 15 22:15:32 localhost kernel: [4294677.399000] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
Feb 15 22:15:32 localhost kernel: [4294677.400000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
Feb 15 22:15:32 localhost kernel: [4294677.400000] PCI: setting IRQ 10 as level-triggered
Feb 15 22:15:32 localhost kernel: [4294677.400000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
```

Floppy is also disabled in fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda1 / reiserfs notail,noatime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda2 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 noauto,user  0 0
#/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0

```

Any ideas would be greate.

Thank you```

```

---

