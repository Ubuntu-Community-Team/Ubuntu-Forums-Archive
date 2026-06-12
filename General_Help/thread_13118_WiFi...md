---
title: "WiFi.."
date: 2005-01-28
forum: General Help
---

### Post by Alt-F4 on 2005-01-28
Hey, i have an ASUS A8V WiFi mobo.... my WiFi works fine in Mandrake and WinXP, but with Ubuntu (LiveCD) it has trouble detecting it during the boot, and i cant seem to set it up once its booted....

Is there any specific process to set up your WiFi connection with Ubuntu?

---

### Post by alastair on 2005-01-31
[QUOTE=Alt-F4]Hey, i have an ASUS A8V WiFi mobo.... my WiFi works fine in Mandrake and WinXP, but with Ubuntu (LiveCD) it has trouble detecting it during the boot, and i cant seem to set it up once its booted....

Is there any specific process to set up your WiFi connection with Ubuntu?[/QUOTE]
 If it works with Mandrake then there must be Linux support - probably a kernel module. You might want to boot Mandrake and do an "lsmod" to identify the module (perhaps check /etc/modprobe.conf).

Looking at Google (search "groups" for "ASUS A8V linux wireless") seems to point to the module being "Ralink 
RT2500" perhaps :

[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

So, the question is - does Ubunto have the module? (rt2500). Do a search under /lib/modules. If not, a LiveCD might not be the best route to your support - but a normal Ubunto install should allow its addition (modprobe rt2500).

---

