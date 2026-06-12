---
title: "hp deskjet 3420???..."
date: 2006-04-05
forum: General Help
---

### Post by orlox on 2006-04-05
Well, I need to get this printer working in ubuntu. Does anyone know how to do this?

---

### Post by Sef on 2006-04-05
Have you tried this:

system > Administration > printing

If the regular HP don't work, try HP (HPLIP)

---

### Post by David Haas on 2006-04-05
oriox--Your HP Deskjet 3420 is supported by Ubuntu Breezy, for the PPD file (driver) for it is installed by default. I locate it in the HP directory at /usr/share/cups/model/foomatic-ppds/HP. The file is:.     HP-DeskJet_3420-hpijs.ppd.gz.  So, you should be able to install the printer with the printer GUI (System > Administration > Printing at the top menu bar) Click "New Printer" and then follow the few directions in the box. Usually when you select your printer from the list after selecting HP, the driver is automatically installed. If not, then click "select driver" and click your way through the directories listed above to get to the HP listing of the above PPD file for your printer.

When the driver is installed, you will see an unzipped copy at /etc/cups/ppd.

Well, I hope this helps you.

David

---

### Post by orlox on 2006-04-05
Thanks!! That worked inmediately...

---

