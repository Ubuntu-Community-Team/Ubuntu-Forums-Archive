---
title: "CUPS does not work..."
date: 2006-01-26
forum: General Help
---

### Post by lleb on 2006-01-26
the user/pw combo in CUPS on the web interface does not work.

i have gone through the "System / Administration / Users & Groups" and added CUPSYS to the "shadow group", i have manually edited the p/w for cupsys and nothing alows me to get access to the web interface for CUPS.

there is no "root" user in *buntu so there is no way to log out of user, and restart X as root so i can not use the GUI tools provided by either Gnome or KDE, and to top it off the printer is not printing every time i tell it to print.

i like a lot of the "ease" of the *buntu project, but to hamstring linux users from being able to gain PROPER access to many of the root level tools to configure printers, or other networkable assets is just bad designe.

now how in the world am i supposed to network out the printer that is connected to my edubuntu system so my CentOS and Debian workstations can gain access to this printer? 

NO CUPS = NO SHARED PRINTING IN LINUX...

*grumble not happy*

---

### Post by rmjokers on 2006-01-26
At some point I purchased a samsung laserjet printer that came with proprietary software to install the drivers.  This software was supposed to modify the CUPS configuration through the web interface.  I found out that Ubuntu intentionally compiles CUPS with the root web configuration interface turned off so that you cant use it to modify the configuration.  The only way to configure CUPS is to use the Gnome printer tool or to manually edit the config file.  This also means I was unable to install the drivers for my printer :(

Note:  There should be a way to manually edit the configuration file to allow sharing of the printer if you cant do this through the gnome interface.

---

