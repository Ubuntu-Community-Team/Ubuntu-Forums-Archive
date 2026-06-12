---
title: "wireless printer doesn't respond to jobs"
date: 2011-10-29
forum: General Help
---

### Post by Tamalin on 2011-10-29
I just bought a Kodak OfficeHero 6.1 Wireless printer/fax machine.  Unfortunately, even thought I can find and connect to the printer through CUPS, when I send it print jobs, the printer doesn't respond (the printer's logs don't even show any job records).  Kodak says I need to install their Home Print and Media Center junkware that came with the printer to print, but can't because it is Windows only and I don't want it anyway.  Does anyone have any knowledge of how I can get this working?

---

### Post by paulnewall on 2011-10-31
The cups filter built into ubuntu 11.10 will not work with this printer.
If you are prepared to compile and install an experimental filter, you could try the new version of c2esp21~rc2 here
[http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)
follow the install instructions in the .tar.gz file
use the ppd file for the Cxxx series printers

---

### Post by paulnewall on 2012-01-14
Now there's a deb file you can easily install here if you have 32 bit ubuntu
[http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)
 
Also a basic scanner driver, but you have to compile that
[http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/]("http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/")

---

