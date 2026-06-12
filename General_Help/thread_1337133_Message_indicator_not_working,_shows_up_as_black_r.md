---
title: "Message indicator not working, shows up as black rectangle"
date: 2009-11-25
forum: General Help
---

### Post by fprintf on 2009-11-25
Since upgrading to Karmic Koala, the new messaging that came with JJ is not working (which it did previously). I am simply getting a black rectangle with rounded corners that will disappear if I mouse over it.  This is for a upgrade install not a brand new installation.

I have searched but am wondering if this has been reported already, and I just don't know the correct search terms. It is on an old IBM ThinkPad T30 with ATI graphics.

---

### Post by mac9416 on 2009-11-25
Hey, fprintf,

This problem has been seen on laptops running Radeon Mobility 7500  since the Karmic upgrade. You can read all about it here: [http://ubuntuforums.org/showthread.php?t=1285406](http://ubuntuforums.org/showthread.php?t=1285406)

The solution, as provided by zainka in that thread, is to add the following lines to your /etc/X11/xorg.conf (If it does not exist, just create it).

> # To avoid unreadable windows.
Section "Device"
	Identifier	"Radeon7500"
	Driver	"ati"
	BusID	"PCI:1:0:0"
	Option	"RenderAccel" "false"
EndSection

Let me know if that works for you!

---

### Post by fprintf on 2009-11-25
Adding the Option "renderaccel" "false" worked perfectly. I can now see the system monitor and any other apps that were previously big black objects on my screen.

Thanks!

---

