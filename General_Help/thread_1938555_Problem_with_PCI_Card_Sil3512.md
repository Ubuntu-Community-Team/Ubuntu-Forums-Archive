---
title: "Problem with PCI Card Sil3512"
date: 2012-03-09
forum: General Help
---

### Post by jgott on 2012-03-09
Hey guys, i just bought a PCI card with the chip from Silicon Image Sil3512. It has two SATA ports. And I connected a Western Digital Harddrive to one of them (it has NTFS as filesystem). The problem is i cant find the drive anywhere.

The fdisk only finds my current drive.

From lshw i get this info:

 *-storage
             description: RAID bus controller
             product: SiI 3512 [SATALink/SATARaid] Serial ATA Controller
             vendor: Silicon Image, Inc.
             physical id: 7
             bus info: pci@0000:01:07.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list rom
             configuration: driver=sata_sil latency=32
             resources: irq:17 ioport:9000(size=8) ioport:9400(size=4) ioport:9800(size=8) ioport:9c00(size=4) ioport:a000(size=16) memory:fb000000-fb0001ff memory:80000000-8007ffff

Is there a way to access to the drive connected to the PCI card?

---

### Post by dik23 on 2012-06-01
Same here:

```
-storage
                description: RAID bus controller
                product: SiI 3512 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list rom
                configuration: driver=sata_sil latency=64
                resources: irq:21 ioport:cf00(size=8) ioport:ce00(size=4) ioport:cd00(size=8) ioport:cc00(size=4) ioport:cb00(size=16) memory:fdeff000-fdeff1ff memory:fdd00000-fdd7ffff
```

```
02:00.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
	Subsystem: Silicon Image, Inc. SiI 3512 SATARaid Controller
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil
```

```
dmesg | tail
[375286.220043] ata7: EH complete
[375286.261645] ata7: hard resetting link
[375286.580039] ata7: SATA link down (SStatus 0 SControl 310)
[375286.580051] ata7: EH complete
[375287.708334] ata8: hard resetting link
[375288.032080] ata8: SATA link down (SStatus 0 SControl 310)
[375288.032092] ata8: EH complete
[375288.121683] ata8: hard resetting link
[375288.440042] ata8: SATA link down (SStatus 0 SControl 310)
[375288.440054] ata8: EH complete
```

sudo fdisk -l shows sda* and sdb* but no sdd* = what is shown when usb is used.

12.04 3.2.0-24-generic-pae  

Drive, esata cable and enclosure work on Win7 and pci card displayed so I'm doubting it's a hardware issue. Have tried with drive formatted with fat32 and ext3 partitions.

Has anyone got any ideas ?

---

