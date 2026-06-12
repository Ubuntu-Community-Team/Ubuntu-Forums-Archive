---
title: "Blinking desktop items after clean 11.04 install"
date: 2011-09-06
forum: General Help
---

### Post by Windows-NoMore on 2011-09-06
I just did a clean install of Ubuntu 11.04 and it all seems to have gone well but after the reboot and the subsequent login, all I get is that multi-color background and a flashing desktop folder.  If I right click on the desktop I get a flashing desktop settings menu but the desktop is otherwise unuseable (no panel either).  I can Ctrl/Alt/F1 to a terminal prompt and can login that way so is there some commands I can run to fix this install?  Thanks.

almost forgot to mention
AMD64
GeForce FX5200 512MB AGP
1.5GB RAM

---

### Post by Windows-NoMore on 2011-09-06
Ok I have figured this one out.  It seems that my graphics card does not like the nVidia 173 driver so choosing Gnome Classic at login I was able to deactivate the driver and roll the system back to the driver from the original install.  I got the message that Unity would not work but I prefer the Gnome layout with the panels I can set myself.  I have used Unity on a previous install so I know it will work but it's the driver that is the cause.

---

