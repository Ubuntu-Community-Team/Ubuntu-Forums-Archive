---
title: "can't get diablo 2 to install"
date: 2011-07-19
forum: General Help
---

### Post by sPiN1 on 2011-07-19
i type wine /media/install/install.exe and it asks me to insert the install disc, when i do so it pops up over and over again. i don't know what's wrong it worked on my older version of ubuntu, now i have the latest and can't get it to work

---

### Post by 3Miro on 2011-07-19
Check winecfg to see if you have the cdrom drive listed under "Drives".

I manually mounted all the CDs one by one to /mnt/cdrom since Nautilus and Thunar would just create /media/install /media/play folders and wine wouldn't recognize those.

---

### Post by sPiN1 on 2011-07-19
i have c: /drive_c
d: /
h: /home/jason
z: /
under drives. 
and if i try to manually open it, i get this message 
Blocked: wine start /unix
The file '/media/INSTALL/INSTALL.EXE' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

so, i drag the install.exe file to my desktop, right click and make it executable and i get an hour glass, and nothing happens. don't make me install windows just for a game, ubuntu!

---

