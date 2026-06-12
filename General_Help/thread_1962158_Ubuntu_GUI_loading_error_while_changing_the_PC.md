---
title: "Ubuntu GUI loading error while changing the PC"
date: 2012-04-20
forum: General Help
---

### Post by Bilal Afzal on 2012-04-20
I had HP DV6850ee on which ubuntu 10.10 was installed. but i have bought a new laptop. I am connecting my hard disk through USB and booting it up using USB boot option. Ubuntu loads in a fine manner but the GUI is not loading. May be because of the graphics driver. 

can any one tell me what could be the solution? because I dont know how can I install the correct graphics driver using command line promt.

---

### Post by Herman on 2012-04-20
You probably just need to boot in 'Low Graphics Mode', first and then if you want you can install a driver specific to the different hardware after your USB Ubuntu has booted.

To get into 'Low Graphics Mode', you scroll down one line in your GRUB Menu and select to boot into 'Recovery Mode', and you will find menus in there which lead to the options to boot in 'FailsafeX' and then either 'Boot in Low Graphics Mode Just for One Session', or 'Reconfigure Graphics'. Then go back and 'Resume Normal Boot'.

As far as I can tell, that process just renames the /etc/X11/xorg.conf and boots Ubuntu with the generic graphics driver. 
If it's easier for you it's also possible to do the same thing by using some other Ubuntu or other Gnu/Linux OS to mount the USB and delete the same file if it's easier. You could just delete the file, but instead of just deleting the xorg.conf file, it might be a better idea to simply rename it so you'll have a backup copy in case you want to boot in the old hardware again, (if you had favorite settings).

It would be wonderful if Ubuntu would run a hardware detection command at boot time and compare it with logs to test if it has been running in the same hardware before and automatically set the appropriate optimal drivers and display settings the user set last time with the same hardware. 

At least the default graphics works well enough to get a display in almost any computer which is good enough for most ordinary tasks. It's only when I want to use GIS software or Google Earth that I need a special graphics driver. Unfortunately though for me I use those programs a lot, so I almost always need to change the graphics driver for whatever PC I boot my USB Ubuntu in. The procedure becomes easier with practice.

---

