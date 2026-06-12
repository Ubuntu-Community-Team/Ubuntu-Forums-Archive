---
title: "Make /dev/tty* devices accessible"
date: 2010-11-03
forum: General Help
---

### Post by rpinsky on 2010-11-03
I want all /dev/tty devices to be accessible to any user. I can manually do a sudo chmod a+rw /dev/tty* and it will make them accessible but when I reboot, it reverts back. Is there a proper place to make this survive a reboot?
 
The actual device I really need accessible is /dev/ttymxb2 (if I could only choose one device).
 
Thanks,
Robert

---

