---
title: "Wacom config anyone?"
date: 2006-03-28
forum: General Help
---

### Post by Mortimer on 2006-03-28
The tablet works fine and pressure works, so the driver is setup ok. The question is, the active zone on the tablet, anyone know how to do this? xsetwacom doesn't seem to do anything but give errors, and setting up options in xorg.conf does something but not the desired thing. I've found some faqs that say TopX/Y BottomX/Y can map this, but maybe those directions are outdated, that doesn't seem to work with these newer drivers. TopX/Y seem to do nothing in xorg.conf. BottomX/Y do something, but not what is said in those faqs. The numbers don't seem to map pixels but maybe the tablet dpi?

Anyone know how to set configure this zone?

---

### Post by davim on 2006-12-29
I have mine working fine. All I did was edit the xorg.conf:

(...)
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
#	InputDevice    "stylus" "SendCoreEvents"
#	InputDevice    "cursor" "SendCoreEvents"
#	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "stylus" "AlwaysCore"
	InputDevice    "cursor" "AlwaysCore"
	InputDevice    "eraser" "AlwaysCore"
	InputDevice    "pad" 
	InputDevice    "Synaptics Touchpad"
EndSection
(...)
Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
#	Option	    "Stylus2" "3"
	Option	    "USB" "on"
	Option	    "InputFashion" "Pen"
	Option	    "Name" "Graphire4 Stylus"
	Option	    "Vendor" "Wacom"
#	Option	    "Protocol" "Auto"
#	Option	    "SendCoreEvents" "on"
#	Option	    "Tilt" "on"
#	Option	    "Device"	 	"/dev/wacom"
	Option	    "Device" 		"/dev/input/wacom"
#	Option	    "Device"	 	"/dev/input/event3"
	Option	    "Mode" "Absolute"
	Option	    "Type" "stylus"
	Option "KeepShape" "on"
	Option "TopX" "0"
	Option "TopY" "0"
	Option "BottomX" "1280"
	Option "BottomY" "800"
	Option      "Threshold" "10"
	Option	    "PressCurve" "50,0,100,50"
#	Option	    "ForceDevice"	"ISDV4"
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
#	Option	    "Stylus2" "3"
	Option	    "USB" "on"
	Option	    "InputFashion" "Eraser"
	Option	    "Name" "Graphire4 Eraser"
	Option	    "Vendor" "Wacom"
#	Option	    "Protocol" "Auto"
#	Option	    "SendCoreEvents" "on"
#	Option	    "Tilt" "on"
#	Option	    "Device"	 	"/dev/wacom"
	Option	    "Device"		"/dev/input/wacom"
#	Option	    "Device"	 	"/dev/input/event3"
	Option	    "Mode" "Absolute"
	Option	    "Type" "eraser"
	Option "KeepShape" "on"
	Option "TopX" "0"
	Option "TopY" "0"
	Option "BottomX" "1280"
	Option "BottomY" "800"
	Option      "Threshold" "10"
	Option	    "PressCurve" "50,0,100,50"
#	Option	    "ForceDevice"	"ISDV4"
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "USB" "on"
	Option	    "Mode" "relative"
	Option	    "InputFashion" "Tablet"
	Option	    "Name" "Graphire4"
	Option	    "Vendor" "Wacom"
#	Option	    "Protocol" "Auto"
#	Option	    "SendCoreEvents" "on"
#	Option	    "Tilt" "on"
#	Option	    "Device"	 	"/dev/wacom"
	Option	    "Device"		"/dev/input/wacom"
#	Option	    "Device"	 	"/dev/input/event3"
	Option	    "Type" "cursor"
	Option "KeepShape" "on"
	Option "TopX" "0"
	Option "TopY" "0"
	Option "BottomX" "1280"
	Option "BottomY" "800"
	Option      "Threshold" "10"
#	Option	    "ForceDevice"	"ISDV4"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  #Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
#  Option        "ButtonsOnly" "on"
#  Option        "Button9" "1"
#  Option        "Button13" "3"
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

---

