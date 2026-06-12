---
title: "Applet Errors and Nagios Error"
date: 2010-05-18
forum: General Help
---

### Post by wsoxfan10 on 2010-05-18
Problems with Ubuntu 9.10. Installed on a Dell Dimension 2400 with P4  processor and 256mb RAM.

 I had Nagios up and running, monitoring  a few printers, a workstation, and a switch with no problems.

 After  I installed libpng, zlib, and mrtg I began getting applet errors. I  downloaded libpng and zlib source code and installed them myself. I  followed the mrtg instructions to install mrtg. I didn't get any errors  when installing so I'm not sure where the problem stems from.

 Here  are the bunch of applet errors I get after every reboot:

The  panel encountered a problem while  loading

 "OAFIID:GNOME_ShowDesktopApplet"
 "OAFIID:GNOME_NotificationAreaApplet"
 "OAFIID:GNOME_IndicatorApplet"
 "OAFIID:GNOME_CloclApplet"
 "OAFIID:GNOME_FastUserSwitchApplet"
 "OAFIID:GNOME_WorkspaceSwitcherApplet"
 "OAFIID:GNOME_Panel_TrashApplet"
 "OAFFID:GNOME_WindowListApplet"

I  tried "apt-get install ubuntu-desktop" and it says ubuntu-desktop  is already at the newest version, 0 upgraded, 0 newly installed, 0 to  remove, 0 not upgraded.

 I am also receiving a "segment  fault" error when attempting to edit the switch.cfg file for Nagios with "gedit /usr/local/nagios/etc/objects/switch.cfg"

 I'm  sort of a noob so I'm not sure what to do. I'd rather troubleshoot and learn something new than reinstall.

 Thanks

---

### Post by machubun on 2010-05-27
Hi, 
Uninstall the "zlib" package and restart the system. The problem should go away. I did the exact same thing you did and got into the problem and on uninstalling got it back :) 

Thanks, 
Mach

---

### Post by athena_acq on 2010-06-25
@machubun Can you tell me how you uninstalled zlib? I had installed zlib by compling the source. Hence, I don't know how to uninstall it. 
So, I just removed the zlib.h file from my /usr/local/include directory. 
This has restored my GNOME menus partially, but not completely. My date and time is still missing and so is the open wondows bar at the bottom.

---

### Post by mc4man on 2010-06-25
```
I had installed zlib by compling the source.
```
Typically if you've installed from a sudo  make install then youd try cd'ing back to your source folder and running 

sudo make uninstall

If the source folder is gone or source has no uninstall available then remove manually

In this case not many files and easily seen in /usr/local

> I just removed the zlib.h file from my /usr/local/include directory. 

That's one - look in /usr/local/lib and /usr/local/share

After removing all then run 
```
sudo ldconfig
```

---

