---
title: "Driver for Epson scanner needed?"
date: 2011-10-24
forum: General Help
---

### Post by randj on 2011-10-24
I have an Epson V300 scanner. When I try to use any scanner program eg Xsane I get the message scanner not connected (seen).
 
Ubuntu 11-04. The scanner has an USB connection. All other USB devices eg priner are seen OK.
 
Have downloaded and installed Image scan ( Avasys), but no luck. When I power up the scanner no lights flash to indicate a connection (as in Windows).
 
Why just this one device?
 
Please help.
 
Randj

---

### Post by crazy bird on 2011-10-24
It looks like that your device is not supported by SANE: [http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON).

Take a look at the website. They migth give a solution.

---

### Post by andied on 2011-10-24
I have been able to get my Epson V500 Photo working by using the drivers at avasys:  
  [http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do)

There are 3 required files from avasys, and I had to also install xsane to get my scanner to work. Also, do not install sane extras.

---

### Post by randj on 2011-10-25
Thanks -  I did not realise that I had to download 3 files from Avasys for this model of scanner.

---

