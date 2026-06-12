---
title: "HPLIP problems"
date: 2009-09-29
forum: General Help
---

### Post by hbbliss on 2009-09-29
I just tried hp-check from a fresh install of 9.04 (with all updates) and got a number of errors with suggestions to run aptitude-install to overcome them. Why is this necessary? Why does not HPLIP come ready to work out-of-the-box? My printer is an HP LaserJet 1100a and I would like to get HPLIP working, especially for the attached scanner. Help will be greatly appreciated.

---

### Post by sgosnell on 2009-09-29
Not everyone uses HP equipment, so the full suite isn't bundled.  It's not that hard to get, though.  You don't need hplip installed to scan, you just need to tell xsane what scanner to use.  If you want to install hplip, you can either open a terminal and type 'sudo apt-get install hplip', or open Synaptic, find hplip, click on the box, select "Mark for installation", and then click Apply.

Or go to [HPLIP download page](http://hplipopensource.com/hplip-web/install/install/index.html), download the latest version, and follow the instructions on that page.  The terminal installer is very good.

---

### Post by hbbliss on 2009-09-29
Thanks for the rapid reply. I checked Synaptic and hpjis, hplip(3.9.2.), and hplip-data are installed. My scanner is part of the HP All-in-one printer (a parallel printer) and x-sane does not recognize it. I ran sudo apt-get install hplip and it said "hplip is already the newest version". If I run an install from the hplip site, will it fix the dependency problems reported for the currently installed version? I do not mind downloading a new version but I kneed to know if this new version will allow me to specify a parallel printer. If not, is there a way to fix the newest version to recognize my hardware?

---

### Post by sgosnell on 2009-09-30
Yes, you can install a parallel printer, but are you sure that's what you have?  I haven't seen a parallel printer in years.  They're either USB or network, and I haven't seen a parallel port on a computer in years.  

Try opening System/Administration/Printing, and click on the Add button.  Try adding a new printer, and have the wizard find the printer.  I've never seen that fail with an HP printer.  It finds my network printer every time, almost immediately.

Alternatively, open HPLIP, and select Setup Device.  It should find the printer and set it up for you.

Do you have the HPLIP icon in your panel?  It should load at startup, but if not, you can have it load through System/Preferences/Startup Applications.

---

### Post by hbbliss on 2009-10-16
I ran a manual install of hplip.3.9.8 and during the configure step added --enable-pp-build to the command line then executed. When I did a hp-setup it gave the chance to specify parallel port.

---

