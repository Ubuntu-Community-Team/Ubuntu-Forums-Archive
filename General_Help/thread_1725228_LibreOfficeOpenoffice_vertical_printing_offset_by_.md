---
title: "LibreOffice/Openoffice vertical printing offset by ~2cm"
date: 2011-04-09
forum: General Help
---

### Post by apochry on 2011-04-09
Hi Guys,

I am using LibreOffice 3.3.2 Final on a 10.10 Ubuntu Laptop.  Everything I print from LibreOffice and Openoffice is printed ~2 cm too high. Printing from other programs as Document Viewer and GIMP is just fine.  It's not a settings problem, I’ve checked everything hundred times.  I am printing on HP Deskjet connected to a wireless router with CUPS 1.4.4 Driver.

Has anyone experienced the same problem? Any help will be appreciated.

Izzo

---

### Post by apochry on 2011-04-23
Well, I fixed the problem by deleting the printer in CUPS and setting it up new. I tried with drivers for other HP printers close to my model and one of them happened to work better than the driver provided for my printer (so now I'm printing on my HP Deskjet 5700 using the 5800's driver).

---

### Post by scania_gti on 2011-11-07
> **apochry said:**
> ...Well, I fixed the problem by deleting the printer in CUPS and setting it up new...
Many thanks! This way to solve "too high printing" work for my too :D
Just go with browser:[URL="http://localhost:631/admin"] Administration - CUPS 1.5.0
[/URL]

---

