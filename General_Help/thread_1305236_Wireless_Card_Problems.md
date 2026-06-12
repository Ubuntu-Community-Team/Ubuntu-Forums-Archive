---
title: "Wireless Card Problems"
date: 2009-10-29
forum: General Help
---

### Post by linuxguy5 on 2009-10-29
Hi,
I just installed Ubuntu 9.10. I am using Wubi on an HP Mini 110. Ubuntu does not detect the wireless card. It used to detect the wirless card in Ubuntu 9.04 through the use of a properitary driver. When I go to Hardware Drivers, it tells me no properitary drivers are in use. Here is the wireless card part of lspci -v
```

01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 1507
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number ff-ff-00-ff-ff-00-00-00
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb


```

I am not sure what to do. I would however, like to congratulate Canonical for a terrific new release. A sound issue in which I couldn't hear without plugging in headphones was fixed.

Thanks.

---

### Post by dummy910 on 2009-10-29
not sure in 910 here as I just installed it a couple of hours ago on this machine, but in 9.04 and earlier, the wireless card fix I always use in Ubuntu is:
```
sudo apt-get install linux-backports-modules-[COLOR=red]jaunty[/COLOR]
```[COLOR=red]*****[/COLOR] of course you would change [COLOR=red]jaunty[/COLOR] to whatever release your using, say [COLOR=red]karmic[/COLOR], [COLOR=red]hardy[/COLOR] etc....

---

