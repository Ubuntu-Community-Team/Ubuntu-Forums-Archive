---
title: "Slot info"
date: 2009-09-13
forum: General Help
---

### Post by Howard Kaikow on 2009-09-13
Does ubuntu contain a prog that lists the information about the AGP/PCI/ISA slots, and what type of card is in slt?

---

### Post by DeMus on 2009-09-13
> **Howard Kaikow said:**
> Does ubuntu contain a prog that lists the information about the AGP/PCI/ISA slots, and what type of card is in slt?

Try lspci in a terminal

---

### Post by Howard Kaikow on 2009-09-13
> **DeMus said:**
> Try lspci in a terminal

Thanx.

Info is listed for the ISA bridge, but not the ISA slots.

Info is listed for only PCI and AGP controllers.

USB Controller
SCSI storage controller
Ethernet controller
VGA compatible controller

No info is listed for either the modem or sound card.

Do I need to use another command?

---

### Post by DeMus on 2009-09-13
> **Howard Kaikow said:**
> Thanx.

Info is listed for the ISA bridge, but not the ISA slots.

Info is listed for only PCI and AGP controllers.

USB Controller
SCSI storage controller
Ethernet controller
VGA compatible controller

No info is listed for either the modem or sound card.

Do I need to use another command?

To get a particular item from the list (for example sound) use:
```
lspci | grep Audio
```

Also you can use
```
lsusb
```
to get info about your Usb connections.

---

### Post by Howard Kaikow on 2009-09-13
> **DeMus said:**
> To get a particular item from the list (for example sound) use:
```
lspci | grep Audio
```

Produces no output.

> **DeMus said:**
> Also you can use
```
lsusb
```
to get info about your Usb connections.

lsusb does not identify the USB card,
lspci does not identify the USB card.

I guess what I am looking for is the linux equivalent of [PC Wizard]("http://www.cpuid.com/pcwizard.php").

PC Wizard identifies thec slots used, but not the card in ach slot.

My problem is tht PC Wizard is incorrectly reporting the slot info on my sister's computer. I was hoping to find an equivalent linux program that she cpould run from a Live CD.

All I really need to know is which slots are free, and of which type is each slot. I want my sister to be able to do this without opening the tower. I am concerned that she might incorrectly report which type of slots are free.

---

