---
title: "touchpad not working AFTER login"
date: 2010-08-15
forum: General Help
---

### Post by svenskmand on 2010-08-15
Ok, so I installed Ubuntu 10.04 on my sisters computer as she is starting her university studies, and this strange error occurred.

Ubuntu boots and hits the login screen, where the touch-pad and keyboard works fine, but when the password is typed in and enter is hit, the touch-pad works for some seconds and then stops working. The keyboard is working fine at all times, and if a usb mouse is connected it also works fine.

I suspect it to be some weird but in the xorg configuration, so I tried to locate xorg.conf, but using the command
```

locate xorg.conf

```
I only got back these directories and files
```

/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz

```
I am not sure how to fix this problem any hints? The touch-pad is a Synaptics so I suspect the changes should be made in the file 10-synaptics.conf but I am not sure, here is the content of the file
```

Section "InputClass"
	Identifier "touchpad catchall"
	MatchIsTouchpad "on"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
EndSection

Section "InputClass"
	Identifier "Dell Inspiron embedded buttons quirks"
	MatchTag "inspiron_1011|inspiron_1012"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "90"
	Option "AreaBottomEdge" "4100"
EndSection

Section "InputClass"
	Identifier "Dell Inspiron quirks"
	MatchTag "inspiron_1120"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "250"
EndSection

Section "InputClass"
	Identifier "HP Mininote quirks"
	MatchTag "mininote_1000"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "20"
EndSection

```

Thanks :)

---

### Post by sanderj on 2010-08-15
Is it the same bug as here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/542063](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/542063) ?

If so, join that bug report.

---

### Post by svenskmand on 2010-08-26
It is not the same problem. The problem I had was that the mouse worked fined when the computer booted and I arrived at the login screen. But as soon as I logged in the mouse stopped working.

I tried to reinstall but that did not solved it at first, but I noticed that it seemed that the mouse only stopped working when I connected to a wireless network :S

But after a couple of restarts after the reinstall the problem was gone, I have no idea what caused it or why it went away again. But the system works now :)

---

