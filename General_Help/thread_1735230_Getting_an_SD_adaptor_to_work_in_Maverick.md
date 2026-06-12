---
title: "Getting an SD adaptor to work in Maverick"
date: 2011-04-21
forum: General Help
---

### Post by saxojon on 2011-04-21
Hello.

I've been using Ubuntu 10.10 for the past couple of months now and I thoroughly enjoy it, but I've seem to eventually come over a problem. I'm on vacation and want to transfer pictures from my camera to my computer. I have a Micro SD adapter (2 GB) that I've tried to put into my SD slot on my computer, but it seems that Ubuntu doesn't recognize it (gotten a bit used to plug & play laziness, I guess). Does anyone know how to make Ubuntu recognize the memory card?

Thanks.

---

### Post by dcstar on 2011-04-21
> **saxojon said:**
> Hello.

I've been using Ubuntu 10.10 for the past couple of months now and I thoroughly enjoy it, but I've seem to eventually come over a problem. I'm on vacation and want to transfer pictures from my camera to my computer. I have a Micro SD adapter (2 GB) that I've tried to put into my SD slot on my computer, but it seems that Ubuntu doesn't recognize it (gotten a bit used to plug & play laziness, I guess). Does anyone know how to make Ubuntu recognize the memory card?

Thanks.

Are you **100% sure** that your SD reader is compatible with the SD card?

---

### Post by saxojon on 2011-04-21
> **dcstar said:**
> Are you **100% sure** that your SD reader is compatible with the SD card?

Well, it used to work when I ran XP on this computer, so I guess so.

---

### Post by Grenage on 2011-04-21
When connected, is it listed under drives?

```
sudo fdisk -l
```

That command should list any attached storage.

---

### Post by saxojon on 2011-04-21
> **Grenage said:**
> When connected, is it listed under drives?

```
sudo fdisk -l
```That command should list any attached storage.

Can't see any difference with it plugged in. Here is the print from the terminal:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d90b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14212   114149376   83  Linux
/dev/sda2           14212       14594     3068929    5  Extended
/dev/sda5           14212       14594     3068928   82  Linux swap / Solaris

---

### Post by Grenage on 2011-04-21
Alas, no; just your existing 120GB hard drive.  I don't have any machines with card readers, but does yours list the device if you type *lshw* in a terminal?

I've always assumed that they simply used the USB bus, and functioned as adapters.

---

### Post by saxojon on 2011-04-21
> **Grenage said:**
> Alas, no; just your existing 120GB hard drive.  I don't have any machines with card readers, but does yours list the device if you type *lshw* in a terminal?

I've always assumed that they simply used the USB bus, and functioned as adapters.

Yeah, it seems like the SD ports are actually USB ports. At least the print corresponds with the number of USB + SD ports on the computer. Following is the USB part of the print, which again (to my knowledge) show no sign that the OS recognizes the inserted memory card.
> 
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:6080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:6060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:6040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:6020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:58544400-585447ff

---

