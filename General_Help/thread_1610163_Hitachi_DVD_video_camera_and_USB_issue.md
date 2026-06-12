---
title: "Hitachi DVD video camera and USB issue"
date: 2010-10-31
forum: General Help
---

### Post by Marzata on 2010-10-31
How to download files from Hitachi DVD video camera (DZ-MV750E) connected with USB cable to Ubuntu? 

When the cable is connected the output of lsusb is: 
Bus 001 Device 005: ID 04a4:0043 Hitachi, Ltd 

The DVD disk recorded with the same camera also can not be loaded in Ubuntu. 

Any ideas how to fix any of the above two issues? 

Thank you.
-- 
Ubuntu 10.04 (lucid)
Kernel Linux 2.6.32-25-generic-pae
GNOME 2.30.2 
Nautilus 2.30.1

---

### Post by Hippytaff on 2010-10-31
If theres no linux driver you will have to use the windows driver with ndiswrapper

[http://dvdcam-pc.support.hitachi.ca/en/download/dl.asp](http://dvdcam-pc.support.hitachi.ca/en/download/dl.asp)
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

---

