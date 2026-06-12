---
title: "Help, My Ubuntu hangs for 3 minutes when start up"
date: 2006-06-21
forum: General Help
---

### Post by widjajayd on 2006-06-21
My ubuntu Hang for 3 minutes between these bold text (mounting root file systems)
then it continue working.

```

Jun 20 20:53:38 ws01 kernel: [4294674.578000]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:pio, hdd:pio
Jun 20 20:53:38 ws01 kernel: [4294674.842000] hda: MAXTOR 6L040J2, ATA DISK drive
[B]Jun 20 20:53:38 ws01 kernel: [4294675.454000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jun 20 20:53:38 ws01 kernel: [4294710.545000] hda: max request size: 128KiB[/B]
Jun 20 20:53:38 ws01 kernel: [4294710.546000] hda: 78198750 sectors (40037 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(100)
Jun 20 20:53:38 ws01 kernel: [4294710.547000] hda: cache flushes supported
Jun 20 20:53:38 ws01 kernel: [4294710.547000]  hda: hda1 hda2 < hda5 hda6 hda7 >
Jun 20 20:53:38 ws01 kernel: [4294711.007000] usbcore: registered new driver usbfs
Jun 20 20:53:38 ws01 kernel: [4294711.008000] usbcore: registered new driver hub
Jun 20 20:53:38 ws01 kernel: [4294711.013000] **** SET: Misaligned resource pointer: d6cfdae2 Type 07 Len 0
Jun 20 20:53:38 ws01 kernel: [4294711.013000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
Jun 20 20:53:38 ws01 kernel: [4294711.013000] PCI: setting IRQ 5 as level-triggered
Jun 20 20:53:38 ws01 kernel: [4294711.013000] ACPI: PCI Interrupt 0000:00:01.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
Jun 20 20:53:38 ws01 kernel: [4294711.014000] ohci_hcd 0000:00:01.2: OHCI Host Controller
Jun 20 20:53:38 ws01 kernel: [4294711.025000] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
Jun 20 20:53:38 ws01 kernel: [4294711.025000] ohci_hcd 0000:00:01.2: irq 5, io mem 0xee800000
Jun 20 20:53:38 ws01 kernel: [4294711.078000] hub 1-0:1.0: USB hub found
Jun 20 20:53:38 ws01 kernel: [4294711.078000] hub 1-0:1.0: 3 ports detected
Jun 20 20:53:38 ws01 kernel: [4294711.179000] ACPI: PCI Interrupt 0000:00:01.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
Jun 20 20:53:38 ws01 kernel: [4294711.179000] ohci_hcd 0000:00:01.3: OHCI Host Controller
Jun 20 20:53:38 ws01 kernel: [4294711.190000] ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
Jun 20 20:53:38 ws01 kernel: [4294711.190000] ohci_hcd 0000:00:01.3: irq 5, io mem 0xee000000
Jun 20 20:53:38 ws01 kernel: [4294711.243000] hub 2-0:1.0: USB hub found
[B]Jun 20 20:53:38 ws01 kernel: [4294711.243000] hub 2-0:1.0: 2 ports detected
Jun 20 20:53:38 ws01 kernel: [4294711.396000] usb 1-1: new full speed USB device using ohci_hcd and address 2[/B]
Jun 20 20:53:38 ws01 kernel: [4294712.370000] SCSI subsystem initialized

```

I only have one ide harrddrive
any idea?

---

### Post by dcstar on 2006-06-21
[QUOTE=widjajayd]My ubuntu Hang for 3 minutes between these bold text (mounting root file systems)
then it continue working.
......
I only have one ide harrddrive
any idea?[/QUOTE]
Check if your drive is actually set to be a "Slave" on the IDE channel, Ubuntu may be searching for a "Master" device and waiting for a time-out.

---

