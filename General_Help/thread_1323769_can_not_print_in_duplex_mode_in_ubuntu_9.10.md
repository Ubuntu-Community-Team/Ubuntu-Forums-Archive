---
title: "can not print in duplex mode in ubuntu 9.10"
date: 2009-11-12
forum: General Help
---

### Post by bilol on 2009-11-12
Hi all,
I have installed Ubuntu 9.10,but I am **unable to take printing in duplex mode**.It is a known fact that the printer supports duplex mode and I took duplex printing in ubuntu 8.04.Here , in 9.10,it shows only two options under duplex mode:(1) off( one sided) (2) ignore.
How can I take duplex printing? Please suggest..

---

### Post by Dark_Stang on 2009-11-12
What's the printer model number?

---

### Post by bilol on 2009-11-12
HP Laserjet 2420

---

### Post by PRC09 on 2009-11-12
When you install the printer via the add printer function about 3 screens in it will list your installable options,duplex printing has to be checked to enable it.System Administration> Printing> New>Select Device>(Printer Port)> Choose Driver > Hope this helps.....

---

### Post by bilol on 2009-11-12
Thank you very much PRC 09;It worked.
Duplex has to be enabled while installing the printer.

---

### Post by dspisak on 2010-01-03
I want to add my experiences with duplex printing.  I also am running ubuntu 9.10, 64-bit.  The printer is a HP 1220C.  It does not have a "duplexer".  I've tried these drivers: hpcups 3.9.12 and hpijs 3.9.8.  Neither driver will print double-sided when that option is selected.  The only way to obtain double-sided or duplex printing is to first print the the odd pages, rotate the printout 180 degrees and reload, then print the even pages.

With XP Pro the duplex option give me duplex prints straight away.

Perhaps the next versions of hpcups or hpijs can have a true duplex printing option.

---

