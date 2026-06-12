---
title: "Virtualbox no loger working on Oneiric"
date: 2011-11-24
forum: General Help
---

### Post by Gingalone on 2011-11-24
Until yesterday my Virtualbox (Win XP on it) worked fine, but today it doesn't work. I get two windows:
-----------------------
1st window:
Failed to open a session for the virtual machine ginguswinn.
The virtual machine 'ginguswinn' has terminated unexpectedly during startup with exit code 1.
Details
Result Code:NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}

2nd window:
Kernel driver not installed (rc=-1908 )

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
-------------------------
What about? What happened since yesterday?

---

### Post by howefield on 2011-11-24
There was an update to the kernel, perhaps that knocked it out.

Have you run the command as directed ?

---

### Post by BC59 on 2011-11-24
Solutions

1. Reinstall VirtualBox from Ubuntu Software Center.

2. Boot (from the boot screen) with the previous kernel.

---

### Post by Gingalone on 2011-11-24
I did what asked by un-working vbox (installed DKMS and run the foreseen command as root) and I got Vbox back working again.
I think (as suggested by howefield) the culprit was the last Ubuntu update (it involved some change in the kernel).

Thanks for help!

---

