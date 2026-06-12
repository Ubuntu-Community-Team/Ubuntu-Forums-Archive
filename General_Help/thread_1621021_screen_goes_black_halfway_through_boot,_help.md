---
title: "screen goes black halfway through boot, help"
date: 2010-11-13
forum: General Help
---

### Post by scimor5 on 2010-11-13
I have an asus netbook with an intel GMA integrated chip. until now i had been using the out of the box drivers, hadn't changed anything, and it worked ok. I tried installing a graphics driver and rebooted. This time i got the command line only, logged in, uninstalled the driver (apt-get remove) and rebooted, now after i choose ubuntu in GRUB an instant after the ubuntu loading screen comes on it goes to black. I'm trying to find a way from within GRUB to get it to do a command-line boot so i could force it to use the default drivers (how would i do this exactly?), but when i press "e" and then put "text" at the end of the "kernel" line it doesn't change anything. so what do i do from here? worst case scenario i reinstall ubuntu. I realize that i probably did something really stupid here. any help or insight you guys can give would be great, thanks.

---

### Post by dcstar on 2010-11-14
> **scimor5 said:**
> I have an asus netbook with an intel GMA integrated chip. until now i had been using the out of the box drivers, hadn't changed anything, and it worked ok. I tried installing a graphics driver and rebooted. This time i got the command line only, logged in, uninstalled the driver (apt-get remove) and rebooted, now after i choose ubuntu in GRUB an instant after the ubuntu loading screen comes on it goes to black. I'm trying to find a way from within GRUB to get it to do a command-line boot so i could force it to use the default drivers (how would i do this exactly?), but when i press "e" and then put "text" at the end of the "kernel" line it doesn't change anything. so what do i do from here? worst case scenario i reinstall ubuntu. I realize that i probably did something really stupid here. any help or insight you guys can give would be great, thanks.

Use the options to boot into recovery mode.

---

### Post by scimor5 on 2010-11-14
recovery mode goes to black aswell

---

