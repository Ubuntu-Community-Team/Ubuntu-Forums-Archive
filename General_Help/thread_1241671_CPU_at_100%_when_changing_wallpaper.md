---
title: "CPU at 100% when changing wallpaper"
date: 2009-08-16
forum: General Help
---

### Post by orangeLemon on 2009-08-16
I've noticed that on Ubuntu when I change my wallpaper the CPU spikes up to nearly 100% (99.6%, 99.4%, etc) when I change wallpapers, and stays that high for about 10-15 seconds even after the wallpaper is completely changed, making the computer nearly unresponsive until it is done. While it is changing it keeps on stalling, the transition effect is by no means smooth at all. Running the command "top" in the terminal tells me that xorg is using about 90% of the processor while I'm changing wallpapers. My computer isn't exactly new, but I would think that it would be more than enough to change a simple wallpaper. At first I thought that it was just when I was changing large wallpapers, but I've noticed that it does the same thing when I change to a blank wallpaper.

System Specs
Processor - 2800+ AMD Athlon 2.08 ghz
Graphics Card - Nvidia Geforce 4 MX Integrated
Graphics Driver - Version 96 installed, Compiz Disabled.
Memory - 512mb (Runs at 25% while changing wallpaper)
File system - ext4
Version - Ubuntu (Gnome) 9.04
Xorg.conf - 
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
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
	Option	"DontZap"	"False"
EndSection

```
If any more information is required let me know.

---

### Post by CatKiller on 2009-08-16
The wallpaper transition in Jaunty is horrible. It would be nice if there was a way to turn it off. I used to run a script at login to randomise the wallpaper, and that stupid transition stretched the login process by another 5 seconds or so. Nasty. KDE manages a similar fade transition absolutely fine, so I have no idea what the problem is with the Gnome one.

---

### Post by lessgov2007 on 2009-08-16
I noticed this as well. For me it only has an issue when compiz is running though. With no desktop effect, or just Metacity compositing it doesn't have the issue.

---

