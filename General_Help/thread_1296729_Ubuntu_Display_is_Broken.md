---
title: "Ubuntu Display is Broken"
date: 2009-10-21
forum: General Help
---

### Post by kogger on 2009-10-21
Firstly, my computer has run into a hardware issue. I have a laptop, but the connection to the screen broke earlier today. I'm planning on getting it fixed soon, but in the meantime I have a computer with a non-working display.

However, I've figured out that I can get it to work if I just use an external monitor. It worked at first, but the monitor had a larger resolution, and for some reason Ubuntu kept running really slowly whenever I tried to open the Display Preferences window to adjust it, and then any changes I did make wouldn't work. In the process I seem to have broken Ubuntu's ability to display anything, as booting up into Linux now yields an external monitor that doesn't detect any signals. I'm currently writing this post from Windows (hitting down and enter a few seconds after pressing Power gets me into Windows, whose resolution works fine).

In case it'll help, here's my xorg.conf file:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2720 900
	EndSubSection
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection
```

I would love to get this fixed; I miss Ubuntu already. :-(

---

