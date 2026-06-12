---
title: "pci=nomsi -What does it do?"
date: 2009-11-15
forum: General Help
---

### Post by billyboy1978 on 2009-11-15
Hello.
I've allways had to add pci=nomsi to my grub for be able to wake up my laptop ( from suspend/hibernate).

Why is so? and what does it do to my system?

thanx :p

---

### Post by Zorael on 2009-11-15
Google is your friend. :3

[http://www.nvnews.net/vbulletin/showthread.php?t=120710](http://www.nvnews.net/vbulletin/showthread.php?t=120710)
[quote=SilentLexx]Message Signaled Interrupts (MSI and MSI-X) (PCI_MSI)

This allows device drivers to enable MSI (Message Signaled
Interrupts). Message Signaled Interrupts enable a device to
generate an interrupt using an inbound Memory Write on its
PCI bus instead of asserting a device IRQ pin.

Use of PCI MSI interrupts can be disabled at kernel boot time
by using the 'pci=nomsi' option. This disables MSI for the
entire system.[/quote]
[quote=Bernhard/Jaxxon]Message Signaled Interrupts (MSI) have the advantage that you don't
need to share physical signal lines on the mainboard because the
PCI/PCIe/PCI-X device issues an "interrupt command" on the PCI/PCIe/PCI-X
bus to the chipset, instead. For the OS, that means that it can assign an
individual interrupt vector for each device rather than polling all driver's ISRs
using the same IRQ line.

Example: in my configuration, a "cat /proc/interrupts" shows (except):
```
Code:
           CPU0       CPU1       
 16:     207031          0   IO-APIC-fasteoi   arcmsr, EMU10K1, nvidia
220:       1608     165138   PCI-MSI-edge      eth0
```
This means that the nvidia card, the sound card and the raid controller
are all sharing the same (physical or logical) interrupt line. If an IRQ #16
drops in, the OS needs to call all three ISRs, because it can't directly
determine which of the devices actually caused the interrupt (or even
all three devices may have caused an interrupt at the same time).
Typically one interrupt drops in and one ISR will actively handle
this interrupt, the other two ISRs will typically only check that they are
not in charge and return early (but nevertheless consume some CPU
cycles).

Sharing interrupts is always a good source of problems, i.e. race-conditions,
or if one driver goes mad and disables the interrupt line, then the other two
driver are gone, too: when the nivida driver crashes in my setup (i.e.
because of overheat) the sound and the access to the harddisks is also gone.
When using MSI, instead, the OS needs to call only one ISR and it is less likely
that a driver problem leads to a complete system failure.[/quote]
And some mentions later down about some machines not being able to wake from suspend if it's toggled on.

---

### Post by billyboy1978 on 2009-11-15
thanx :)

---

