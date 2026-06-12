---
title: "Crashes(if you can call them that)"
date: 2012-08-29
forum: General Help
---

### Post by Skididdy on 2012-08-29
I just installed Ubuntu on my PC because I'm in the middle of upgrading from an old, busted hard drive.  Everything runs fine except for two things.  My "dash home" button causes my screen to flash about seven times and makes the text on my screen jumble and the whatnot.   Alt+Tab does the exact same thing.  It's not really fatally crashing, but it's quite annoying to Alt+Tab out of habit or try and access my start menu only to be met by 45 seconds of intermittent screen flashing that locks my computer up.

Oh hey, in the process of posting this I also found out that my win key causes the bug as well.  Any help would be greatly appreciated!

EDIT: I've determined that all other buttons on my Unity bar work just fine.  I'm not really a Linux guy, so I haven't the foggiest what it might be... this has confused me further.

---

### Post by dino99 on 2012-08-29
well you does not tell which ubuntu is installed nor which graphic card/chipset is used.

the first thing to do is:

- glance at possible usefull warnings/errors logged into .xsession-errors (ctrl+h to unhide that file) and into /var/log/

- make some cleaning:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a

and the latest notes:
 are you only using genuine ubuntu packages ?
 have you made some custom settings ?

---

### Post by Skididdy on 2012-08-29
> **dino99 said:**
> well you does not tell which ubuntu is installed nor which graphic card/chipset is used.

the first thing to do is:

- glance at possible usefull warnings/errors logged into .xsession-errors (ctrl+h to unhide that file) and into /var/log/

- make some cleaning:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a

and the latest notes:
 are you only using genuine ubuntu packages ?
 have you made some custom settings ?

Graphics is XFX Radeon HD 6850, using 12.04.1.  It's a clean install of Ubuntu from their own website and I haven't changed a thing.  Sorry I didn't include it earlier, I guess I should have read the sticky.

---

### Post by Skididdy on 2012-08-29
I suppose it's permissible to bump if we haven't gotten an answer? I tried what the above user said and it proved to be unfruitful.

---

