---
title: "enable fglrx in 9.10 ?"
date: 2009-10-31
forum: General Help
---

### Post by simartem on 2009-10-31
How can i use fglrx for my ATI Radeon onboard VGA display driver ?
I dont know how to set it up and enable the driver..
The file xorg.conf is empty in /etc/X11..

---

### Post by dummy910 on 2009-10-31
I used the default upgrade xorg.conf file on the machine i type this reply to and all is well on this box, openGL etc work fine. 

The Card on this box is an **ATI Technologies Inc RV350 AP [Radeon 9600]**

> #   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"ati"
EndSection


make sure ya reboot or at least restart the x server for changes to take effect

---

