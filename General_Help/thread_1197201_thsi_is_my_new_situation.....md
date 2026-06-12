---
title: "thsi is my new situation...."
date: 2009-06-25
forum: General Help
---

### Post by jake16424 on 2009-06-25
installed linux mint 7, 

ran fine from USB now i can't get my display drivers to work worth a dang.

keeps saying restart X server, i do and it still wont let me in the X server settings.

oh

can someoen tell me the command to get NVclock up and working?

think its like

GTK Nvclock settings or something like that.

oh and idk why but CTRL ALT BACKSPACE will no longer reset my X server..... >.> this is retarded....

---

### Post by jake16424 on 2009-06-25
Can't find NV-CONTROL extension!
Disabling OpenGL tweaking..

installed all packets that i had on the live version on my USB, mind you it ACTUALLY WORKED until i installed it for keeps.......

anywho that's the message i get when i try and launch the Nvclock to up my fan speed so i don't get a unstable overheating system.

---

### Post by ad_267 on 2009-06-25
Ok so how did you install the drivers?

And you can enable Ctrl+Alt+Backspace by adding this to /etc/X11/xorg.conf:
```
Section "ServerFlags"
    Option "DontZap" "False"
EndSection
```

---

### Post by jake16424 on 2009-06-25
> **ad_267 said:**
> Ok so how did you install the drivers?

And you can enable Ctrl+Alt+Backspace by adding this to /etc/X11/xorg.conf:
```
Section "ServerFlags"
    Option "DontZap" "False"
EndSection
```

what?

im not very verside in terminal talk >.>

i got everything working with my drivers, so meh.. 

just got to install all the other stuff i had going, idk why the drivers wouldn't activate, but i don't think CTRL ALT BACKSPACE works still idk what happened there =(

---

### Post by Tyke91 on 2009-06-25
heh... open up /etc/X11/xorg.conf with the text editor of your choice.

Copy/Paste that in there. just make sure not to put it INSIDE another section

Xorg disabled control alt backspace by default for some reason... Alt+SysRQ+K does almost the same thing, but if you put that dontzap line into your /etc/X11/xorg.conf you can use control alt backspace again

---

### Post by ad_267 on 2009-06-25
Ctrl+Alt+Backspace has been disabled by default in Ubuntu. You can enable it by adding those lines to the /etc/X11/xorg.conf file.

You can do this by pressing Alt+F2 and running "gksu gedit /etc/X11/xorg.conf" and adding those lines to the bottom of the file, then saving it.

---

### Post by jake16424 on 2009-06-25
> **ad_267 said:**
> Ctrl+Alt+Backspace has been disabled by default in Ubuntu. You can enable it by adding those lines to the /etc/X11/xorg.conf file.

You can do this by pressing Alt+F2 and running "gksu gedit /etc/X11/xorg.conf" and adding those lines to the bottom of the file, then saving it.



its already here


# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier     "Configured Monitor"
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
	Option         "NoLogo" "True"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "keyboard"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

[COLOR="Red"]Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
[/COLOR]

---

