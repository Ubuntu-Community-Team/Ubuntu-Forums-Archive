---
title: "Failed to start X-server problem"
date: 2006-03-24
forum: General Help
---

### Post by cloudRunner on 2006-03-24
Hey guys, I just installed Ubuntu as a dual-boot with WinXP on a second hard drive on an AMD 64 machine (I installed the 32-bit version).  The GRUB bootloader installed find and I can get into Windows.  I can also "get into" Ubuntu, but the whole GUI interface isn't coming up.  I get a dialog box saying

> 
"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

And viewing the output, I saw a couple of errors at the bottom:

> 
"Skipping /usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No symbols found."  

So I'm guessing it doesn't have the video drivers to display?  During the setup, it never prompted me to configure the X server.  I'm new to Ubuntu so I'm not sure what to do.  Any help is appreciated.  Thanks.

---

### Post by dermotti on 2006-03-24
type **sudo dpkg-reconfigure xserver-xorg** from command line

select **vesa** for your video driver
Most the other stuff you can just go with the default selections.

Then startx or reboot.

---

### Post by cloudRunner on 2006-03-24
That did it.  Thanks a lot!

One more minor thing... whenever I choose to reboot my pc from Ubuntu, it never quite shuts off... I have to manually power down the system and turn it back on.  If I do a complete shut down it shuts off though.  Any thoughts on this?  Many thanks.

---

### Post by dermotti on 2006-03-24
Give it like 5 minutes and see if it reboots. I know on my system i get a screen of garbage graphics for like 5 minutes before my system kicks over and reboots.

---

