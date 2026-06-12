---
title: "Installation/Boot Freeze"
date: 2006-03-21
forum: General Help
---

### Post by seniorquico on 2006-03-21
I have used Red Hat before to run a simple web server, but I'm pretty much new to using Linux. I figured I'd give Ubuntu a try with all the buzz I've been hearing about it, so I downloaded the 5.10 install CD. The install process seems to work ok, except toward what I would expect is the "end" of the install process. The screen is titled (in the top left corner) "Ubuntu Configuration", and the progress bar goes through installing/configuring different packages.

Once it reaches the "100%" state, a couple messages appear beneath the blue screen. The last one I can catch is something like, "Starting gnome-manager" (I think). But then the screen clears, and a white underscore curser appears for a few seconds. Then the cursor freezes and the system is locked. With no where to go, I restart the computer. Now, it boots up as if it is loading the OS. It goes through the graphical Ubuntu loading screen. When I would expect the desktop/login page to appear, the system freezes (again, white underscore held solid in top left corner).

So, from the GRUB boot loader, I tried the "recovery mode" option. This successfully boots and gives me console access. But I don't know if that even means anything. I've tried a few different burned CDs at different burn speeds (just in case), but they all do the same thing. Normally I can piece my way through something, but not being familiar with Linux and with so few installation options, I can't figure out if it is a problem with how I'm installing or what. If anyone could provide some assistance or point me in the right direction I would appreciate it.

Kyle

---

### Post by nanotube on 2006-03-21
well, this smells to me like the x server does not play nice with your video card. try booting into recovery mode, and editing your /etc/X11/xorg.conf and setting some conservative options (like 16bit color, lower screen resolution, and using the vesa driver instead of whatever it may be set to use) and then reboot and see if that worked.
(of course, back up your xorg.conf file first, by making a copy).
search forums for editing xorg.conf to find more detailed instructions, if you need them. :)

---

### Post by akudewan on 2006-03-21
After you reboot the computer, you get a grub screen, so hopefully, the install process is successful. You also noticed that the last message on the screen is something like "starting gnome-display-manager". This leads me to believe that the problem is either with the X server or gdm.

When the blinking underscore appears on the screen, try pressing Num lock, and see if the LED on the keyboard glows. If its working, then you can try to press "Ctrl + Alt + F1". This will take you to the first console. You can login from here. Try to type ```
 sudo /etc/init.d/gdm restart
``` over here, and see what happens.

Also, which graphics card do you have. And is your monitor very old?

Edit: Nanotube beat me to the post ;)

---

### Post by seniorquico on 2006-03-21
Thanks for the help! I read through the /etc/X11/xorg.conf file, and ended up finding out that it was loading a different graphics card. The computer I'm using has an embedded graphics card (an Intel chipset) and a PCI ATI Rage 128 pro card. I pulled the ATI card out of the box, and I plugged the video cable into the Intel card, and everything booted ok.

So I guess I need to figure out how to change all the settings to get the system to use the ATI card. Reading posts on this board, and reading through the xorg.conf file, I have a couple questions. How can I determine the identifier for my specific video card, and how do I determine the bus the card is running on? Or, is there an easier way to changing the video card in the system other than manually editing the xorg.conf file? Thanks a bunch for the help.

---

