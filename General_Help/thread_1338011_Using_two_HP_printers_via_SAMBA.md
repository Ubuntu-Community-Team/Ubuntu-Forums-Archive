---
title: "Using two HP printers via SAMBA"
date: 2009-11-26
forum: General Help
---

### Post by david-emm on 2009-11-26
I have a laptop using Ubuntu 9.10. On another WIN XP laptop there are two HP printers, a HP1015 laserjet for general black/white printing and a HPPSC1510 for scanning and colour printing.
I have connected to both printers from my Ubuntu laptop using "Windows printer via SAMBA" and can print a test page perfectly to each printer (one in black/white and one in colour). However when using GIMP or F-Spot all jobs are sent to the HP1015 regardless (where the jobs for the HPPSC1510 fail) even though I have selected the HPPSC1510 printer. On the WIN XP laptop the HP1015 is connected via DOT4_001 and the HPPSC1510 is connected via USB001.
Any help is appreciated

---

### Post by david-emm on 2009-11-26
Seems I've found an answer. Both printers use the same driver ( hpijs3.9.8 ) and both printers have to be switched on to allow the system to select the correct printer. If only the PSC1510 is on and the 1015 is off the system puts the print job ito the wrong queue on the WIN XP machine. 1015 seems to work OK if the PSC 1510 is off though. Maybe this is because the 1015 was installed first and is the default printer

---

