---
title: "Help! Modified /etc/X11/xorg.config, now no GUI"
date: 2010-08-18
forum: General Help
---

### Post by squig on 2010-08-18
I was trying to disable touchpad click, added a section to /etc/X11/xorg.config, and now the OS never starts up, the laptop just runs... This is my second day with the machine, I've done a ton of setup but haven't yet setup a backup utility... is there any way for me to just go in and change the file back to the way it was? 

Any help greatly appreciated. Will send cookies. ;)

Squig

---

### Post by Ocxic on 2010-08-18
hold shift while booting, and select the recovery option, edit your file, then reboot

---

### Post by squig on 2010-08-18
Awesome! You saved my a&%. Please send me a private message with address for cookies. :)

---

### Post by worksofcraft on 2010-08-18
I had heard you can simply delete or rename xorg.conf and everything works just fine again after rebooting. I tested it and it a virtual machine on virtualbox had no objections to it missing.

I noticed there is a /usr/lib/X11/xorg.conf.d folder so perhaps that has settings that take precedence?

---

