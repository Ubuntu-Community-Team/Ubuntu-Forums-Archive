---
title: "Need the driver for old ATI Rage laptop graphics card..."
date: 2006-04-30
forum: General Help
---

### Post by enigma_0Z on 2006-04-30
Ahh... I can't find it on my own, so I'll ask here...

What module would give me direct rendering with an *old* ATI card. Specifically a ATI Rage Mobility M3 (AGP 2x) card. There's the r128 module, but AFAIK that is for Rage 128 card. Or am I mistaken?

Would the fglrx driver work? It claims to work only with Radeon 8500+, no Rage cards included... Thanks.

---

### Post by pepijn on 2006-06-08
Same thing for me. I have a powerbook g4 with a Rage Mobility M3 AGP 2x. I'm not planning to play games or heavy rendering but currently the display will only work with 1024x768. 

Is there a driver for this card??

---

### Post by mtbhucker on 2007-03-25
Exact same problem. Can't get full screen res. It does not appear in the list of resolution settings.  There must be an update for the driver for this old Powerbook G4 with ati mobility radeon 128 to allow full screen res.

Any help out there to be had?

---

### Post by az on 2007-03-25
To get acceleration on really old cards with not a lot if ram is often possible.  By default, Ubuntu will use the highest resolution and that will allocate all the ram to 2D graphics and not enough will be left for DRI.  Memory managment is not dynamic on those old cards.

Boot into recovery mode and reconfigure X to use a lower resolution and/or color depth.  Start X and try again.

dpkg-reconfigure xserver-xorg

init 2

---

### Post by Chappy7777 on 2007-03-25
The best place I know of online to find drivers for anything is [www.driverguide.com](www.driverguide.com)

Go there w/the info re:your card and you should find your driver(s).

God bless, Chappy

---

### Post by az on 2007-03-26
> **Chappy7777 said:**
> The best place I know of online to find drivers for anything is [www.driverguide.com](www.driverguide.com)

Go there w/the info re:your card and you should find your driver(s).

God bless, Chappy

The linux driver for all the old ATI cards is already part of the kernel.

It's a configuration problem.

---

### Post by WolfWitch on 2007-04-10
[www.driverguide.com](www.driverguide.com) is great to a degree, however- their "free" sign-up takes you through a wonder-filled world of pop-ups and banner ads, as does trying to actually download anything from them. I won't accuse them directly, but I also noticed a marked increase in spam to the email account I used to sign up with them. I also have yet to actually successfully install a driver provided by them (admittedly only a handful of them on really old equipment).

As *az* already said- the driver is already built-in, as they are for most video cards that aren't on the bleeding edge of newness. Usually with older cards the issue is with the actual card (and video memory) or display detection. Get as many details as you can about your card and monitor (especially its supported resolutions and refresh rates, and run through *dpkg-reconfigure xserver-xorg* (as already suggested by az).

---

### Post by hack124x768 on 2007-04-12
In x, you just use the ati driver. It autodetects the proper driver (radeon, r128, maybe others) and uses that. For resolutions higher than 1024x768, try editing your /etc/X11/xorg.conf file. (look about 3/4 of the way down) Change this:

"1024x768" "800x600" "640x480"
to this:
"1280x1024" "1024x768" "800x600" "640x480"

There will be a few. If it doesn't work, you may need to lower your screen color depth. This is also needed for 3D stuff. Change this:

Default depth 24
to this:
Default depth 16

I wrote all this without the config file infront of me so it may be a little off.

---

### Post by Maxwell7 on 2007-06-24
Hey, thanks ..  that did the trick for me too :D 

I was "fixing" an old laptop from a friend with a ATI card. The screen was only partially filled.  But now it works .

---

### Post by katon on 2007-11-07
> **hack124x768 said:**
> In x, you just use the ati driver. It autodetects the proper driver (radeon, r128, maybe others) and uses that. For resolutions higher than 1024x768, try editing your /etc/X11/xorg.conf file. (look about 3/4 of the way down) Change this:

"1024x768" "800x600" "640x480"
to this:
"1280x1024" "1024x768" "800x600" "640x480"

There will be a few. If it doesn't work, you may need to lower your screen color depth. This is also needed for 3D stuff. Change this:

Default depth 24
to this:
Default depth 16

I wrote all this without the config file infront of me so it may be a little off.

hey, i did this changed depth to 16because i can't change the resolution more than 800x600 and it doesn't work  

what can i do?  i have ATI Technologies Inc Rage Mobility P/M AGP 2x  at my laptop old one Ibm Celeron 500 thinkpad this is my xorg:

[I]
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Rage Mobility P/M AGP 2x"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility P/M AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
[/I]

---

