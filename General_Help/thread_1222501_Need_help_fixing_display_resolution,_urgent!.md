---
title: "Need help fixing display resolution, urgent!"
date: 2009-07-25
forum: General Help
---

### Post by intx on 2009-07-25
I've reformatted twice.

I've completely reinstalled drivers multiple times.

Most of the time I've been stuck in 640x480 or 800x600.

I enabled the proprietary drivers via Hardware Drivers and managed to get it to 11xx x 864? .

I've since lost that and I'm stuck at 1024x768. 


Here's my xorg.conf

```

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync 30-82
	VertRefresh 56-76
	Option "DPMS"
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
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"True"
EndSection


```


I added the Option and Horizsync and VerticalRefresh by myself. I got the values for the latter two using ddcprobe.

Here's my output from that:

```
vbe: VESA 3.0 detected.                 
oem: NVIDIA                             
vendor: NVIDIA Corporation              
product: Crush50 Board - c51pvg0 Chip Rev
memory: 131072kb                         
mode: 640x400x256                        
mode: 640x480x256                        
mode: 800x600x16                         
mode: 800x600x256                        
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid:
edid: 1 3
id: 5140
eisa: WDE5140
serial: 00000000
manufacture: 20 2006
input: sync on green, analog signal.
screensize: 38 30
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1280x1024@60
ctiming: 1152x864@75
dtiming: 1280x1024@70
monitorrange: 30-82, 56-76
monitorserial: &#65533;
monitorname: L1928NV

```

When I first installed, I just downloaded the drivers from the nvidia website and they worked. I had 1280x1024, it looked great.

Updates made them fail pretty bad.

I'm at my wits end, I need help! What can I do?

I've tried using the reconfigure.

---

### Post by madsmeg on 2009-07-26
do you have the nvidia config app in your menu (cant remember where it is exactly, at work at the moment)

You should be able to configure your desktop through that.

---

### Post by wojox on 2009-07-26
In a terminal:

```
gksudo nvidia-settings
```

Edit and save.

---

