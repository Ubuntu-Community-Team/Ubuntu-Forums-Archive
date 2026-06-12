---
title: "Karmic:  Print Dialog Delay &quot;Getting Printer Status...&quot;"
date: 2009-11-19
forum: General Help
---

### Post by N00bB00b on 2009-11-19
I did a fresh install of KK, reinstalled the printers, and now I have a problem with an HP printer.  The add printers function finds it, and auto-selects the HPLIP driver.  However this driver checks the printer's status every single time the print dialog comes up, causing a delay of several seconds while I'm waiting to hit the print button.  The AppSocket connector does not seem to suffer from this problem.

I assume that KK is choosing HPLIP by default for a reason, but this behavior is really annoying.  Any fix suggestions?

---

### Post by N00bB00b on 2009-11-19
Ugh.  OK, - for this printer (HP LJ 8000N), KK waits for the status update regardless of the connection type I use, apparently.  This is painful.

---

### Post by N00bB00b on 2009-11-20
More info:  If the HP printer is the default printer this problem happens.  If I have another printer set as the default and I switch to the HP, then the delay doesn't happen.

---

### Post by bilderbuchi on 2009-12-18
happens for me too (HP network printer). any solution yet?

---

### Post by N00bB00b on 2009-12-18
No, and it is VERY frustrating.

---

### Post by w.kazimierczak on 2010-01-11
There's a bug report on this: [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/475845](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/475845).

The solution might be to change the driver from "recommended" to "Foomatic/Poscript" type.

---

