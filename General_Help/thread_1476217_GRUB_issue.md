---
title: "GRUB issue"
date: 2010-05-07
forum: General Help
---

### Post by Luftfuß on 2010-05-07
First i would like to apologize if this is already posted (i checked and couldnt find it), anyways, I recently got a GRUB error that went like this: 'error Grub_puts_ not found' so I reinstalled GRUB and Ubuntu (10.04) is booting nicely. Then earlier today i tried booting into Windows 7 (installed to 2nd partition of the first hard drive {hd0,1}) and the screen goes blank, then flashes the blinking underscore in the top left corner (like its loading or waiting for input) then just brings me back to GRUB menu.  I figured it was just a menu.lst problem so i opened it ($  gksudo gedit /boot/grub/menu.lst) and added the windows 7 entry, which wasn't there at all and adjusted the timeout to 21 secs, saved and rebooted to check and not only did the win7 still not boot but it didnt adjust my timeout. I checked the file and my changes are still there (even upon reboot). So i downloaded startupmanager and the changes it made worked, but since i cant edit my windows entry with it i cant boot windows.

---

