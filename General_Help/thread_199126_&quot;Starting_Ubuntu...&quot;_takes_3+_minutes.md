---
title: "&quot;Starting Ubuntu...&quot; takes 3+ minutes"
date: 2006-06-18
forum: General Help
---

### Post by widjajayd on 2006-06-18
My Ubuntu 6.06 takes 3+ minutes on booting (Mounting root file systems)

and it stuck on line
running /scripts/local-top
"hdc: no response (status = 0xe3), resetting drive"

I only have 1 drive (no usb), how I fix this.

I checked from /var/log/messages
```
Jun 17 12:05:03 S01 kernel: [4294672.464000] hda: MAXTOR 6L040J2, ATA DISK drive
Jun 17 12:05:03 S01 kernel: [4294673.076000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[B]Jun 17 12:05:03 S01 kernel: [4294718.558000] hdc: no response (status = 0xe3), resetting drive
Jun 17 12:05:03 S01 kernel: [4294723.760000] hdc: no response (status = 0xe3)[/B]
Jun 17 12:05:03 S01 kernel: [4294724.079000] hda: max request size: 128KiB
Jun 17 12:05:03 S01 kernel: [4294724.081000] hda: 78198750 sectors (40037 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(100)
Jun 17 12:05:03 S01 kernel: [4294724.081000] hda: cache flushes supported
Jun 17 12:05:03 S01 kernel: [4294724.081000]  hda: hda1 hda2 < hda5 hda6 hda7 >
Jun 17 12:05:03 S01 kernel: [4294724.523000] usbcore: registered new driver usbfs
Jun 17 12:05:03 S01 kernel: [4294724.524000] usbcore: registered new driver hub
Jun 17 12:05:03 S01 kernel: [4294724.527000] **** SET: Misaligned resource pointer: d5d3cae2 Type 07 Len 0
Jun 17 12:05:03 S01 kernel: [4294724.527000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
Jun 17 12:05:03 S01 kernel: [4294724.527000] PCI: setting IRQ 5 as level-triggered
Jun 17 12:05:03 S01 kernel: [4294724.527000] ACPI: PCI Interrupt 0000:00:01.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5

```

Thanks

---

