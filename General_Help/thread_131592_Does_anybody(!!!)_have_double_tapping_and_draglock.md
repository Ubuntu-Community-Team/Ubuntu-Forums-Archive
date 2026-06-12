---
title: "Does anybody(!!!) have double tapping and draglock working with synaptics touchpad..."
date: 2006-02-16
forum: General Help
---

### Post by hyperpsyched on 2006-02-16
I so miss draglock under windows. Please help, I am getting carpal tunnel holding down my mouse button and trying to slide my other finger over the mouse pad... I mean just look at my hand! 

:-k 

Seriously, enough with the mouse pad twister. If you have your mouse pad double tappin' and draglockin' then for the love of god help! Please post the section of your xorg.conf file (and also if you are using xorg and not XFree86) where you have the synaptics pad configured.

This would be swell. You could even double tap and draglock your way down the xorg.conf file before you paste it to the post just to show off :D

---

### Post by jimisdead on 2006-02-17
I don't have time to make this pretty but try adding this to your xorg.conf:

> 


Section	"InputDevice"
	[INDENT]Identifier	"Alps Glidepoint"
	Driver		"synaptics"
	#Option		"CorePointer"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	#Option		"Device"		"/dev/input/mouse1"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"on"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"600"
	Option		"FingerLow"		"25"
	Option		"FingerHigh"		"30"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"MaxDoubleTapTime"	"180"
	Option		"ClickTime"		"100"
	Option		"FastTaps"		"1"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"20"
	Option		"MinSpeed"		"0.2"
	Option		"MaxSpeed"		"2.5"
	Option		"AccelFactor"		"0.06"
	Option		"EdgeMotionMinZ"	"30"
	Option		"EdgeMotionMaxZ"	"160"
	Option		"EdgeMotionMinSpeed"	"15"
	Option		"EdgeMotionMaxSpeed"	"15"
	Option		"EdgeMotionUseAlways"	"0"
	Option		"UpDownScrolling"	"1"
	Option		"LeftRightScrolling"	"1"
	Option		"TouchpadOff"		"0"
	Option		"GuestMouseOff"		"1"
	Option		"LockedDrags"		"1"
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"0"
	Option		"LTCornerButton"	"2"
	Option		"LBCornerButton"	"2"
	Option		"TapButton1"		"1"
	Option		"TapButton2"		"1"
	Option		"TapButton3"		"3"
	Option		"CircularScrolling"	"0"
	Option		"CircScrollDelta"	"0.08"
	Option		"CircScrollTrigger"	"0"
	Option		"CircularPad"		"0"
	Option		"PalmDetect"		"1"
	Option		"PalmMinWidth"		"10"
	Option		"PalmMinZ"		"200"
	Option		"CoastingSpeed"		"0"[/INDENT]
EndSection



then comment out the old Synaptics Touchpad InputDevice and it's associated entry in the serverlayout section then add:

	[INDENT]InputDevice 	"Alps Glidepoint"[/INDENT]

to your serverlayout section

and make sure you have the **xserver-xorg-input-synaptics** package installed...

you can then use either the ksynaptics or qsynaptics packages (after installing it) to configure scrolling etc.

...worked for me.

---

### Post by hyperpsyched on 2006-02-17
oh man... I actually haave an ALPS device but after alot of searching in forums and google I have read alot of stuff about different drivers and snd an alps.patch which may or may not require a kernel rebuild (shudder).

I have xorg-driver-synaptics installed, should I really try the XFree driver. Do you know anything about the alps.patch?

---

### Post by jimisdead on 2006-02-18
touchpads aren't really my speciality but I'm pretty sure mine is an ALPS device too and it's working perfectly with the xorg.conf mods I posted earlier.

... and sorry but the xserver-xorg-input-synaptics package is a dapper release, but I've read the equivalent breezy package works too. Try looking at this page - [http://www.rtr.ca/dell_i9300/](http://www.rtr.ca/dell_i9300/) - and scroll down to 'installation notes' to find the touchpad information.

---

### Post by hyperpsyched on 2006-02-18
How stable are you finding dapper? I might upgrade if it means I can get draglock working. Tried your config and read the dell stuff and nothing worked, though I learned a bit about the configuration of input devices.

---

### Post by hyperpsyched on 2006-02-18
Thanks jimisdead... another user posted a great thread about configuring ALPS pads and with you xorg.config as well I have dragock working... woo hoo.:-D

---

