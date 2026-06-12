---
title: "Cannot print from gedit"
date: 2011-09-25
forum: General Help
---

### Post by Keith_Beef on 2011-09-25
A curious problem...

I cannot get gedit to print to my Epson printer, nor to a PDF file; but I can print from Libre Office, glabels and gimp (using the defualt option, not Gutenprint).

I turned on "Save debugging information" in the Cups server settings, but what should I be looking for in /var/logs/cups/error_log to help troubleshoot?

---

### Post by jsmumma on 2012-11-19
I have the same problem. Beginning around 28 OCT 2012 I could no longer print or print preview from gedit (2.30.3). I tried logging out and back in with no effect. Found an Ubuntu bug report about this, but, unfortunately, the bug reporter was rebuffed due to alleged lack of adequate information. I reinstalled gedit via SPM, but no joy. I reinstalled both gedit and gedit-common via SPM, but still no joy. I tried print preview of a text file open in gedit and got blank pages for all 235 pages (based on checking a lot but not all of them) except page 2. Weird.

This problem is specific to gedit (or something upon which gedit alone relies) because lpr, other editors, LibreOffice, OpenOffice, etc. print fine to the same printer (HP Deskjet 6940 interfaced via LAN). This is a case where something that works flawlessly for years just suddenly stops working. The system is a HP Pavilion zv6000 laptop running Ubuntu 10.04 LTS.

I downloaded [http://ftp.gnome.org/pub/GNOME/sources/gedit/3.2/gedit-3.2.6.tar.xz](http://ftp.gnome.org/pub/GNOME/sources/gedit/3.2/gedit-3.2.6.tar.xz). I tried building it, but ran into errors that I frankly do not have the desire to pursue to ground. So, I'm stuck with a broken gedit that will not print.

---

