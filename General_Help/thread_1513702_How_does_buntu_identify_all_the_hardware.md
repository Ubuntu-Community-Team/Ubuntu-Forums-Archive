---
title: "How does *buntu identify all the hardware?"
date: 2010-06-19
forum: General Help
---

### Post by JKyleOKC on 2010-06-19
This may seem like something too far down in the hardware for this forum, so feel free to move it to a better place if one exists. I need to know, in some gory detail, just how the boot-time code determines what devices are where on the PCI and PCI-express bus(es). I have a network card that's simply not being detected at all, most of the time, but it does show up occasionally -- which tends to rule out a real hardware problem although it doesn't completely exclude that possibility. My suspicion is that it's a problem with the kernel driver module for the card, but in order to pin it down more accurately and possibly fix it, I need to know just what the boot-time code is looking for, and where...

Specifically, the NIC chip involved is RealTek's R8168B, and the r8168 and r8169 drivers for the chip show up often in trouble reports -- but so far nobody has pinned down the root cause of the troubles. I'm willing (and able) to dive into the mess and try my hand at a cure, but I need a firm starting point. Having completely disassembled MSDOS back at versions 3.1 and 4, and contributed to two books about its internals, I'm quite familiar with assembly language code and dealing with hardware registers, but I've not found anything more than very general descriptions of the hardware detection process. FWIW, I'm working with Hardy 8.04.4 LTS but I suspect that if I can pin the problem down, the fix will apply to later kernels also...

---

### Post by dcstar on 2010-06-20
> **JKyleOKC said:**
> This may seem like something too far down in the hardware for this forum, so feel free to move it to a better place if one exists. I need to know, in some gory detail, just how the boot-time code determines what devices are where on the PCI and PCI-express bus(es). I have a network card that's simply not being detected at all, most of the time, but it does show up occasionally -- which tends to rule out a real hardware problem although it doesn't completely exclude that possibility. My suspicion is that it's a problem with the kernel driver module for the card, but in order to pin it down more accurately and possibly fix it, I need to know just what the boot-time code is looking for, and where...
.........

Personally I would go into the BIOS and see if the card is being assigned a shared interrupt that may be confusing the kernel.

You should also run the **update-pciids** command to see if this helps.

---

### Post by JKyleOKC on 2010-06-20
Thanks for the suggestions!

I did update the pci.ids list this morning and it had grown significantly. In particular, it now includes a number of sub-listings for the r8168 devices. However running lspci doesn't show any difference -- and since lshw doesn't even show the board's existence I have no idea which of the three PCI Express bridges it might be on!

I suppose a next step would be to search the driver source code for any of the PCI ids that are now listed, but it would certainly help if I knew how the boot-time code searches the bridges to get the ids from the hardware...

---

### Post by JKyleOKC on 2010-06-23
bump

---

