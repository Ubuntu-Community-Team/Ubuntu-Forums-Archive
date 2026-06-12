---
title: "Help on PCI interrupt routing."
date: 2012-07-09
forum: General Help
---

### Post by j3r on 2012-07-09
Hi all, i have a PCI framegrabber card which requires me to set the Slot ID and INT#.
By default, the jumpers (on the card) are set to Slot 2 and INTB.

But my host PC automatically assigns the interrupt for PCI INTA, INTB, INTC and INTD.

How do i know, and set the interrupt routing to the desired configuration for my frame grabber card.

Cheers
Thanks in advance!

---

### Post by Redblade20XX on 2012-07-09
To solve your first problem, you can try and disable the automatic pci routing.

Take a look here: [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

- Red

---

