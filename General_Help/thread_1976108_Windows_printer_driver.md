---
title: "Windows printer driver"
date: 2012-05-08
forum: General Help
---

### Post by megabuffen on 2012-05-08
Is there a way to use a printer printer driver for Windows in Ubuntu? I'm trying to get both grayscale and color printing to work with a Konica Minolta Bizhub C20.

---

### Post by 3rdalbum on 2012-05-08
Windows printer drivers won't work in Ubuntu. Sorry. If there are no native drivers, and CUPS doesn't have an appropriate driver, you may have to run Windows in a virtual machine for your printing needs.

---

### Post by Cheesemill on 2012-05-08
Try this linux driver:
[www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-amd64/openprinting-ppds-postscript-konica-minolta_20100531-1lsb3.2_all.deb](www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-amd64/openprinting-ppds-postscript-konica-minolta_20100531-1lsb3.2_all.deb)

---

### Post by megabuffen on 2012-05-13
The problem is that while the printer does support Postscript, color/grayscale must be selected on the printer itself. It is all hidden a few levels down in the menu so it's inconvenient to say the least. The printer is used by a lot of different people so it has to 'just work'.

I'm thinking I could go with a virtual machine. Something like Windows 95 would have a tiny footprint and still allow me to share the printer on the network. Would this setup allow me to print both color and grayscale using samba?

How does samba printing work anyway?

---

### Post by afrodeity on 2012-05-23
The above package doesn't have a ppd for Bizjet 210. Please help.

---

### Post by afrodeity on 2012-06-18
This worked [http://www.openprinting.org/printer/Generic/Generic-PCL_6_PCL_XL_Printer](http://www.openprinting.org/printer/Generic/Generic-PCL_6_PCL_XL_Printer)

---

