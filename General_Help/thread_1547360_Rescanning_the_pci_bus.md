---
title: "Rescanning the pci bus"
date: 2010-08-06
forum: General Help
---

### Post by tictran on 2010-08-06
We have a device (a demo card with an FPGA and other goodies on it) installed in our system.  The command "lspci" sees the card but we need to rescan the bus after FPGA reconfiguration and set up the address spaces for memory map i/o to actually use the card.  

We think rebooting the system would do it but that seems rather drastic, especially for a development project that will be making changes very regularly.

This used to be done by hotplug but that is long gone.  It was allegedly replaced by module-init-tools but all those seem to do is take care of adding and listing modules already included with the kernel, nothing to do with rescanning the pci bus.

Any thoughts about how to do this?

We are on karmic koala.  

Thanks in advance!

---

### Post by wdeburch on 2011-09-13
Hello tictran,

I have exactly the same issue. As this is a fairly old thread, have you found a way to rescan the pci bus without rebooting?

thanks

---

### Post by tictran on 2011-09-13
Alas, no, we were never able to figure it out -- had to reboot every time.  After a while we got the card software more reliable so were able to reload it and reuse the changed software without having to rescan.

Sorry!

---

### Post by Rubi1200 on 2011-09-13
Thread closed. The OP is unlikely to return to a thread more than a year old.

If you need support, please start your own thread.

---

