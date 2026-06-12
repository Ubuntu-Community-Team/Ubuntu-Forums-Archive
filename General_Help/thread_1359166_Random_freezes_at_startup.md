---
title: "Random freezes at startup"
date: 2009-12-19
forum: General Help
---

### Post by keda on 2009-12-19
I've just bought a M2N68 plus mother board, Athlon II x2 240 processor for my comp but can't seem to get the OS (Kubuntu Jaunty) which was installed and worked fine before. I've tried a Karmic Kubuntu live cd which worked fine on this comp, but fails on my new comp. I've also tried a few things suggested on various sites when googling for the problem I have but not found anything that exactly fits my problem. 

The first thing that showed up when I started was Firmware Bug: powernow K8: your BIOS does not provide ACPI_PSS objects in a way that Linux understands
- this was solved by enabling ACPI and those objects in the CPU config in the BIOS
After this it freezes during the splash in seeminly random locations. At some points it was even able to start checking the disc, but freezed at 4% or so.
after googling for solutions, I've found that after pressing esc during grub, and selecting recovery I get as far as

Begin Waiting for root file system... ...
forcedeth: Reverse Engineered nforce ethernet driver version 0.61.
ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
forcedeth 0000:00:07.0 INT A -> Link[LMAC] -> GSI 23 (Level, low) -> IRQ 23

and freezes there.

with acpi=off it freezes at input: AT Translated Set 2 keyboard as /device/platform/i8042/serio0/input/input3

with noapic it freezes at
Begin: Waiting for root file system... ...

Any help would be appreciated, Thanks.

---

### Post by keda on 2009-12-20
Anyone?

---

