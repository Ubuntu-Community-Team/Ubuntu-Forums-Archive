---
title: "Problems getting X to recognise wacom on tablet PC"
date: 2006-05-17
forum: General Help
---

### Post by kgomm on 2006-05-17
Hi,

I have Breezy Badger installed on my HP TC4200 tablet PC and am having problems getting X to recognise my wacom pen.

I installed the necessary packages (even did an update of the kernel and installed wacom-kernel-source). I found the wacom device under /dev/ttyS14 so that when I started wacdump I got the standard screen and the numbers reacted to my pen moving across the screen. I did the recommended setserial command and edited my /etc/X11/xorg.conf file as per the many examples on this forum and restarted. The tablet did not respond to the pen. The log in /var/log/Xorg.0.log shows that wacom is loaded.

It seems that X "blocks" the pen: after restarting X with the configured xorg.conf, wacdump starts but I cannot influence the output with the pen. If I remove the wacom specific lines from my xorg.conf and restart X, wacdump runs OK again.

Does anybody have any tips/hints at all. I've tried tweaking my xorg.conf in many small ways with no result. I'm very close to giving up and trying my luck with SuSE 10.

Cheers,
Kath

---

### Post by frodon on 2006-05-17
You should this guide : [http://ubuntuforums.org/showthread.php?t=175029](http://ubuntuforums.org/showthread.php?t=175029)
brutimus may be able to help you.

---

### Post by kgomm on 2006-05-18
I've already implemented what was suggested in that thread. Tonight I will gather my xorg.conf file and other wacom configuration details and will post the details tomorrow. Hopefully, one of you out there might see the problem...........

---

