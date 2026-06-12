---
title: "HP DESKJET D2660 and Ubuntu 10.04"
date: 2011-09-28
forum: General Help
---

### Post by t0p on 2011-09-28
Before I bought a HP Deskjet D2660 printer, I checked for Ubuntu compatibility on [Openprinting.org]("http://openprinting.org").  That site is currently down for maintenance; but as I recall, it said that the D2660 *is* compatible with Ubuntu.

But I can't make it work with Ubuntu.  My computer detects the printer, and even goes as far as "adding" printing jobs to the queue.  But the printing never happens, no matter how long I give it (even overnight, curses be upon it!).  I've had to install Windows XP in VirtualBox just so I can use the printer.

I don't know what to do to make the printer work directly with Ubuntu 10.04.  The VirtualBox "solution" is slow and ungainly and I hate it.  Can anyone help?  Cheers!

---

### Post by Tamlynmac on 2011-09-28
I had a similar problem (different printer) and downloaded/installed the HPLIP driver directly. For your printer it's available [here]("http://hplipopensource.com/hplip-web/models/deskjet/deskjet_d2600_series.html"). Just don't forget to reboot both the printer & the PC after installing.

If you need any help installing, try using this [wizard]("http://hplipopensource.com/hplip-web/install_wizard/index.html"). 

In the future if your checking to confirm Linux compatibility with HP printers, you might wish to start [here]("http://hplipopensource.com/hplip-web/supported_devices/index.html").

Good Luck & hope this helps.

---

