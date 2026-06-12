---
title: "Nvidia Grphics card issue."
date: 2009-11-19
forum: General Help
---

### Post by maconga on 2009-11-19
I have just installed xubuntu 9.10 with Wubi... I had a resolution of 800x600 when I installed from the CD. I then installed a NVIDIA accelerated graphics driver (version 96) from the Hardware Drivers, did a restart, and now I am in 640x400 resolution. I can not increase the resolution.

I have the following Nvidia software installed
"nvidia-glx-96"  
"nvidia settings"  
"xserver-xorg-video-nv"

My Video card is a 

Nvidia Geforce 4 440MX SE 64MB
PCI slot


And idea how to fix this?

---

### Post by moe_syzlak on 2009-11-27
You need to change the resolution by manually editing the /etc/x11/xorg.conf file. Here is a copy of my xorg.conf; I have a working nvidia geforce mx 4000 in my computer. The only thing that you need to modify in this configuration file are the input device sections (for mouse and/or KB) and the "BusId" of your Geforce MX4000. [SIZE="7"][COLOR="Red"]The 'BusId' must be changed.[/COLOR][/SIZE]

You will know the BusId from the output from 'sudo lspci.' lspci puts the port of the graphics card in hexadecimal, but you have to change the values from hexadecimal to decimal in order for it to work in the xorg.conf congfiguration file.Post all output from "sudo lspci" and your xorg.conf so that I can tell you what info to put in the respective section.

```


 Section "Screen"
 	Identifier "Default Screen"
 	Device "Configured Video Device"
 	Monitor "Configured Monitor"
 		SubSection "Display"
 			Depth 24
		 	[COLOR="Lime"]Modes "1024x768_60" "1280x1024_60" "1400x1050_60" [/COLOR]
	 		Option "AddARGBGLXVisuals" "True"
 		EndSubSection
EndSection


Section "Device"
	Identifier "Configured Video Device"
	[SIZE="7"][COLOR="Red"]Busid "PCI:0:15:0"[/COLOR][/SIZE]
	Driver "nvidia"
	Screen 0
EndSection
 
 Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "us"
 EndSection

 Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 EndSection
 Section "ServerLayout"
 Identifier "Default Layout"
 screen 0 "Default Screen" 0 0
 EndSection
 
 Section "Extensions"
 Option "Composite" "Enable"
 EndSection


```

---

### Post by D3ath on 2009-11-27
Shouldn't he be able to run nvidia-settings.. or even in system > administation > nvidia settings... and change the config in there...

---

### Post by ROY.G.BIV on 2009-11-27
Run "sudo nvidia-xconfig".

---

### Post by moe_syzlak on 2009-11-27
I got a 'lil tip for you guys, that does not work. nvidia-xconfig will not update that information. Well... it will spit out an xorg.conf, but it will not work. That's why I said you have to modify the xorg.conf manually. I tried configuring Xorg via the Nvidia supplied user dialog but it was a no go. I did that approximately 2 months ago. I tried "my method" like yesterday, and it worked. Then I starting hitting the forums to see who I could help based on if they had the same problem as me... or not.

You know how Linux can be sometimes.

---

