---
title: "HPLIP option not present when setting up printer"
date: 2010-04-20
forum: General Help
---

### Post by Qbeta on 2010-04-20
I just built a system and put a fresh install of ubuntu 9.10 on it.  I have two other systems with 9.10 as well.  On both of them the printer (an HP Officejet Pro 7680 set up directly on the network) is shown as an HPLIP printer with a URI that starts with hp:/net/ . When trying to set up this printer on the new machine the option for HPLIP is not present and the URI starts with dnssd://.  I can only set up as and LPD Network Printer or an Appsocket/JetDirect network printer.  Yes I have the hplip stuff installed on the new machine.  My main concern is actually using the scanner function with Xsane.  The other two machines scan just fine, the new one can't find any devices.  I think this must be connected with the lack of HPLIP functions.  This is with the AMD64 bit version of 9.10, BTW.

---

### Post by Qbeta on 2010-04-20
And it appears I've solved the problem.  There's a package called hplip-gui.  When you install it, you can then add an hplip printer/scanner/fax/ etc...  The only thing that went wrong is that it couldn't find the ppd file for the fax, which I don't use anyway.  The gui tool actually tells you all kinds of neat stuff like the ink levels too.  What I don't get is why the other machines were able to use hplip without ever having hplip-gui installed.

---

