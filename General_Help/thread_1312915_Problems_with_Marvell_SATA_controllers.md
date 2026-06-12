---
title: "Problems with Marvell SATA controllers?"
date: 2009-11-03
forum: General Help
---

### Post by manthony121 on 2009-11-03
I cannot boot the LiveCD of Ubuntu 9.10 on my desktop system.  The disk works fine on my laptop, and on my desktop at the office.  When I installed 8.04 on my desktop, there was a problem with the installation failing, and winding up on a screen with a prompt for busybox/initramfs.  The thread exploring this issue talked a bit about problems with support for some SATA chipsets, the Marvell being among them.  The system now books 8.04 without problems, since including "irqpoll" to the boot options.

Now I am looking at chasing down what seems to be an issue with low-level drivers on my mobo.  The mobo is an Intel D975XBX2, and has several SATA HDDs and a SATA DVD R/W attached.  When I enable printout of the boot procedure, booting from the 9.10 LiveCD hangs with alternating messages of "ata6: link slow to respond" and "ata6: SRST failed".  This seems awfully suspicious for another problem with the SATA chipset.

Is anyone else having problems with this motherboard?  Does anyone have a list of boot options that might help?

---

