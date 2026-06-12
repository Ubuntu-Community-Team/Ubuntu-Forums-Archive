---
title: "Starting in terminal and removing\resetting ati display defaults."
date: 2010-02-02
forum: General Help
---

### Post by axelswe on 2010-02-02
After switching the display properties in ATI catalyst and rebooting my display doesnt work properly. Only the background is drawn at an 90 deg. angle. But the system starts (u can hear IM notifucations from pidgin).

Will booting in to terminal and deleting the ati.conf files solve my problem. And how would i go about doing that

Thanks in advance
-------------------------------------
[Solved]
Ok guys, i found a way. Booted up linux from a live CD. Found the xorg.conf file. It had the monitor orientation as "left". I changed it to "normal", saved the file. and rebooted. And we are back on track.

PS. how do i change the "status" to solved in the thread listnings?

---

