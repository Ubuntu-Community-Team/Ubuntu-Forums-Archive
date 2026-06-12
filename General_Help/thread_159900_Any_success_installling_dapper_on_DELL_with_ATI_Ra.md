---
title: "Any success installling dapper on DELL with ATI Radeon X600"
date: 2006-04-13
forum: General Help
---

### Post by emamm on 2006-04-13
Hello

I have just bought a dell with ATI Radeon X600. When I tried to install kubuntu dapper, the installation proces didn't go far; it got stucks on the usb part during the kernel load.

I tried mandriva 2006;  it worked but not the X-server stuff.

Any ideas?

Many thanks

Ed

---

### Post by souki on 2006-04-13
I have a laptop with a Radeon Mobility X600
dapper installs and runs smoothly on it
don't you have an option to bypass the usb detection phase?

---

### Post by emamm on 2006-04-14
I don't know how to do that?  Would you?

Ed

---

### Post by uteck on 2006-04-17
When you boot the install disk, do NOT press enter.  Instead read the screen and press F2 (or is it F3?) to get to the kernel options to type in so it boots with thoughs options.

Or, you could try turing off the USB in the BIOS, then turn it on after the install.

---

### Post by dapperjohndoe on 2006-05-21
Ubuntu Linux does not support ATI's Radeon X600 graphics card. I guess we will have to accept it and use another Linux... :(

John

---

### Post by Israfel on 2006-05-21
Yeah, ubuntu seems to have issues with ATI; I had to mess with my laptop to get it to work.

---

### Post by dapperjohndoe on 2006-05-30
[QUOTE=Israfel]Yeah, ubuntu seems to have issues with ATI; I had to mess with my laptop to get it to work.[/QUOTE]How did you solve the problem?

John

---

### Post by meowmeow on 2006-06-01
Hi

I have got a ATI Radeon X600 (RV370) card on my Dell Dimension 9150. Dapper works all fine with dual monitor. I installed the Alternate install CD in text mode and copied the following xorg.conf into /etc/X11:


# Xorg configuration created by system-config-display

Section "ServerLayout"
Identifier "Multihead layout"
Screen 0 "Screen0" LeftOf "Screen1"
Screen 1 "Screen1" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
Option "Clone" "off"
Option "Xinerama" "on"
EndSection

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d
EndSection

Section "Module"
Load "dbe"	
Load	"i2c"
Load	"bitmap"
Load	"ddc"
Load "extmod"
Load "fbdevhw"
Load "glx"
Load	"int10"
Load "record"
Load "freetype"
Load "type1"
Load "dri"
Load	"vbe"

EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
Option "XkbModel" "pc105"
Option "XkbLayout" "ch"
Option	    "XkbVariant" "de_nodeadkeys"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "IMPS/2"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Dell 1905FP (Analog)"
HorizSync 31.0 - 83.0
VertRefresh 56.0 - 76.0
Option "dpms"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "Monitor Vendor"
ModelName "Dell 1905FP (Digital)"
HorizSync 31.0 - 83.0
VertRefresh 56.0 - 76.0
Option "dpms"
EndSection

Section "Device"
Identifier "Videocard0"
Driver "radeon"
VendorName "Videocard vendor"
BoardName "ATI Technologies Inc R423 UI [Radeon X600PRO (PCIE)]"
BusID "PCI:1:0:0"
Option "MonitorLayout" "TMDS, TMDS"
Option "CRT2Position" "LeftOf"
Screen 0
EndSection

Section "Device"
Identifier "Videocard1"
Driver "radeon"
VendorName "Videocard Vendor"
BoardName "ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)]"
BusID "PCI:1:0:1"
Screen 1
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x1024"
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device "Videocard1"
Monitor "Monitor1"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x1024"
EndSubSection
EndSection

Section "DRI"
Group 0
Mode 0666
EndSection

Heve fun!

Meow

---

