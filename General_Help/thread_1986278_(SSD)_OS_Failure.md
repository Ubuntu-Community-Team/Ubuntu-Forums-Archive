---
title: "(SSD) OS Failure"
date: 2012-05-24
forum: General Help
---

### Post by XBMC old School on 2012-05-24
Hey All,
 
*See setup in my signature.*
 
A few weeks ago I change my bios setting from IDE to AHCI. Then little by little my install would crash & freeze-up. Now it won't boot at all. When my bios pops up the drives are showing as working. So could i install Ubuntu 12.04 and repath the /home folder and be good? Is the AHCI setting bad for the XFS filesystem? Or should i just reformate and setup the /home with datalinks?

---

### Post by XBMC old School on 2012-06-01
Dump

---

### Post by Redblade20XX on 2012-06-01
Switching from ide to ahci can really mess up the data configuration on any drive attached to the same controller. I'm not currently aware of any way to retrieve that data but any fix will need to reformat the entire drive. If you decide to cut your losses and clean install, keep the ahci setting enabled. It helps the ssd with trim support.

Here is a link that should help you with ssd configurations:
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

-Red

---

