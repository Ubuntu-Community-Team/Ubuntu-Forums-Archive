---
title: "Problem with installing two printers."
date: 2010-01-25
forum: General Help
---

### Post by Evzin on 2010-01-25
I need to connect 2 Epson Styles C110 printers to same computer. However cups seems does not distinct them. When i have first pritner sucessfuly installed in CUPS it get usb://EPSON/Stylus%20C110 address. Now when i plug second printer in and try to add it (using CUPS web interface) it doesnt work since second printer seems get same adress: usb://EPSON/Stylus%20C110. Now i do know that on this copmuter was previously installed ArchLinux and everything was working fine, so this must be some Unbuntu specific problem. Which is really sad since it *need* to make them both work in same time... Is there any suggestions how to fix it?

---

### Post by ajgreeny on 2010-01-25
I don't know if it will work but can you go to System ->Administration ->Printing, open one of the printers and rename it as something slightly different to the name given it by the system.  That may mean that the second printer is installed with the system name and now shows separately from the original.

Worth a try; I don't have two printers to try it out, but will be interested to see if it does work.

---

### Post by Evzin on 2010-01-25
Tried this, did not help. Printers still have same device-URI which i cant (or dont know how to) edit.

---

### Post by Evzin on 2010-01-25
Ok, i seems found the solution. Aparently if you have several printers of same model (at least this applies on Epson printers) CUPS will not be able to distinguish them. Unloading "usblp" kernel module solves this problem.

---

### Post by miltondp on 2010-12-28
Evzin, what version of Ubuntu are you using? I have Lucid. Have the same problem here with Samsung printers. Did you blacklisted usblp module?

---

