---
title: "Eagle from Cadsoft"
date: 2009-11-03
forum: General Help
---

### Post by Jbike on 2009-11-03
Eagle was recently updated from V4.16r2 to V5.4 in 9.10. Unfortunately for me, my professional license does not work on this version. When I run v4.16 from  cadsoft.de, all is well except the video is all messed up only when  3d effects are turned on... This is not the case for Ubuntu's synaptic installation (you guys fix everything).  Can I copy the v4.16 binary over the Ubuntu installed v5.4 binary? I think I can figure this out, but while I am here, where would this executable be located at?  

Thanks, 
Jbike

---

### Post by Giblet5 on 2009-11-03
That only works (sometimes) when an application is statically linked which eagle is not.

If you just love the eye-candy, I would try the pro version under KDE and see if it behaves there. ```
sudo apt-get install kubuntu-desktop kdebase kdeadmin
```

Configure the kdm session manager; it provides more functionality than gdm. At the login screen, click the menu and select KDE for the session, then log in.

If it messes up under KDE, I would set up a separate electronics/cad work account that has 3D effects disabled.

---

### Post by Jbike on 2009-11-03
Thanks for your help... I happen to know that it doesn't work in kde either. I'm going to dig a bit on this one. 

Jbike

---

### Post by Jbike on 2009-11-05
I believe that this is my answer... found on the cadsoft site:
[https://bugzilla.novell.com/show_bug.cgi?id=227337](https://bugzilla.novell.com/show_bug.cgi?id=227337)

See below for all who need to go back to v4.16r2 so their professional license will still work. 

Jbike

[I][COLOR="Blue"]For solving these issues, please check the file xorg.conf. Usually it's located in /etc/xorg or /etc/X11. If it is the case that the composite extension is enabled or not explicitly disabled in the file, change the corresponding section or add the following lines:

Section "Extensions"
       Option "Composite" "Disable"
EndSection

Further information can be found at [https://bugzilla.novell.com/show_bug.cgi?id=227337](https://bugzilla.novell.com/show_bug.cgi?id=227337)

Disabling the Composite Extension on Linux systems that work with xorg-x11 packages of version 7.3 also avoids "X Error" messages that are shown while starting or closing EAGLE 5.x in a bash window.

In the case the display gets corrupted when scrolling up or down in one of the Editor windows or in the EAGLE Control Panel, set the environment variable XLIB_SKIP_ARGB_VISUALS to 1.
This can be done, for example, with the help of a shell script:

  #!/bin/sh
 export XLIB_SKIP_ARGB_VISUALS=1 
 /usr/bin/eagle[/COLOR][/I]

---

