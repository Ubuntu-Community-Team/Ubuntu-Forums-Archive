---
title: "Failing to install printer"
date: 2011-03-27
forum: General Help
---

### Post by ubu10 on 2011-03-27
Sorry, my search led me nowhere, hence this post.
I had been using HP 710C printer on my desktop being connected by parallel-to-USB connection. The location of the printer was /dev/usb/lp0.
Today I installed another printer HP deskjet 1050, which is working fine on my system. But, 710c is no longer working. Its device url is being displayed as usb://unknown/. It is no longer accepting the url that worked earlier (/dev/usb/lp0). Besides, lp0 is now being displayed as 0 bytes.

Both the printers connect via USB to the same USB port (obviously, one at a time).
Please see the description at CUPS.

> Description:    HP710C
Location:    myname-GA-880GM-UD2H
Driver:    HP DeskJet 710C Foomatic/pnm2ppa (recommended) (color, 2-sided printing)
Connection:    usb://Unknown/
Defaults:    job-sheets=none, none media=iso_a4_210x297mm sides=one-sidedI tried deleting the printer and reinstalling it, but to no avail. I have little or no idea of linux. Any help would be thanked.

---

