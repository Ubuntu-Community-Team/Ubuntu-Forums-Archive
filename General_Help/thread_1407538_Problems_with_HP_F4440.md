---
title: "Problems with HP F4440"
date: 2010-02-15
forum: General Help
---

### Post by skrap on 2010-02-15
Deskjet-F4400-series
--------------------
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: usb://HP/Deskjet%20F4400%20series?serial=CN9C1CK70705C5
PPD: /etc/cups/ppd/Deskjet-F4400-series.ppd
PPD Description: HP Deskjet f4213 Series hpijs, 3.9.2
Printer status: printer Deskjet-F4400-series is idle.  enabled since Mon 15 Feb 2010 10:05:34 AM EST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

My question is how do I get the printer installed in hplip?  I can print but cannot scan.  xsane will not recognize printer. I think it has something to do with the cups backend. But, I do not know how to fix.

Jaunty 64bit 2GB Ram 350GB HD

---

### Post by skrap on 2010-02-15
I had to remove hplip that came with Jaunty and download and install hplip-3.9.6 to get everything working. 

Skrap

---

