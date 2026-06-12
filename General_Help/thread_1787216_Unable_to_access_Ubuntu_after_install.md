---
title: "Unable to access Ubuntu after install"
date: 2011-06-20
forum: General Help
---

### Post by Caerulax on 2011-06-20
My prior experience has only been with NeXTSTEP/OpenStep and OSX.

Installed 10.04 successfully via USB flash drive onto ASUS EEE PC 701 (4GB)
The bottoms of some windows were cut off due to screen size.
I downloaded 10.10 for netbooks and saved that ISO to a USB flash drive
I read how to upgrade 10.04 to 10.10 within Ubuntu and thought I would try that first.
Had a running out of space warning, but it supposedly updated and presented itself for reboot.

Upon a reboot all that appears is a black screen with a grey bar at the bottom with the correct time on its right and at the extreme right an icon of a page(?) with an X on it; in the center of the screen is the frozen cursor on a grey rectangle with the computer’s name and above the name the same icon of a page(?) with an X on it.  [http://i1082.photobucket.com/albums/j380/Caerulax/GNOME_issue.jpg](http://i1082.photobucket.com/albums/j380/Caerulax/GNOME_issue.jpg)
	
When this first happens there is a temporary message in the upper right, which fades after a few seconds.  The message is:
"Install problem!
 The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator."

I have read some threads about that message, but have only found them in situations where the person could use a terminal window to try various solutions.  

In my case, I cannot get beyond this screen.  I have tried rebooting from the original USB flash drive which had installed an apparently fully functional Ubuntu 10.04 and the result is the same.  I used a friend’s Windows Vista to load FreeBSD on another USB flash drive – in the hopes that if the 10.04 install was looking for, or finding, the GNOME Power Manager on the Eee 701 it wouldn’t consider that it was already installed (albeit damaged) and skip installing the one on the flash drive, that the FreeBSD would instead install its own power manager…  The same screen was all I got.

I have not found anything in the BIOS that helps.

I cannot get the original ASUS Support DVD to appear on my friend’s Vista (insert/request admin password/but no sign of the app) and have therefore not been able to reinstall the 701’s install.

Would consider zeroing the 4GB, but I do not know how to do that or make it seen by the Vista to do it.  I need no data on the machine.

I have pushed the recessed reset button, removed the battery overnight, removed the 512MB RAM for a few minutes – none of these things made any difference.

No keyboard shortcuts work.  The power button is the only way to start or quit it.

---

### Post by vader95 on 2011-06-20
I would use unetbootin from vista and put make the flash drive bootable and make it so ubuntu is the os.  then install it from the flash drive.

---

### Post by Caerulax on 2011-06-21
Thank you.

I had done that and the result was the same.  UNetbootin was what I used to make each of the USBs bootable.

---

### Post by vader95 on 2011-06-21
to zero the drive, you need a special program, just google search for write zeros to drive.  Windows should see the drive automatically.

---

