---
title: "Boot problem because of ipod"
date: 2012-03-09
forum: General Help
---

### Post by Pigish on 2012-03-09
First of all hello and thank you for any help. (sorry but i'm a noob)
 
I ran an 10.10 ubuntu system and after an ios 5 update my ipod didn't respond any more. So stupidly i removed the libimobiledevice1 driver to try and reinstall it. It turned out to remove my graphics card drivers aswell causing ubuntu not to boot and removing the gnome display manager. I managed to fix the display manger as it now says [OK] but after trying to reinstall the graphic driver and updating on the way to 11.04 i am left with no hope.  At the moment the computer is stuck at trying to load even when i try to boot with an installation disc. I can get to terminal but when i try pressing shift nothing happens.
 
thank you again

---

### Post by donkyhotay on 2012-03-09
If you can't boot from an installation disc then you either have a problem with the disc or something physical with your computer. First thing I would try would be to disconnect all possible boot devices (starting with the iPod) from the computer and then try turning it on both with and without the installation disc. If it boots then it means the computer is getting confused by the iPod (possibly trying to treat it as a regular hard drive). If problem still persists try booting both with and without the installation disc with only keyboard, mouse, monitor and power cord connected. If you can't boot from installation disc with the system in that state then you probably have a HW failure somewhere.

---

