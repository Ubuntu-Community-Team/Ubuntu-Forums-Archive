---
title: "Need xscreensaver on only one screen"
date: 2012-09-07
forum: General Help
---

### Post by dustinr on 2012-09-07
Hello,

I am needing to have xscreensaver to run on only one of my two screens. My thoughts as to do this is to run it on only the :0.0 X display, however that display includes both of my screens. So then I am needing to create a separate X Screen for my two monitors. I have not been able to create the two separate x screens. I edited my xorg.conf script and I have followed some guides but I cant get it to work.

I am using ubuntu 10.10 with intel i915 sandy bridge video. Any help will be greatly appreciated.

Below is my xorg.conf.

```

Section "ServerLayout"
        Identifier      "Layout"
	Screen		"DefaultScreen"
	Screen 		"TopScreen" RightOf "DefaultScreen"
        InputDevice     "touchscreen-2500" 		"CorePointer"
        InputDevice     "touchscreen-2700" 		"CorePointer"
EndSection

Section "InputDevice"
        Identifier      "touchscreen-2500"
        Driver          "evdev"
        Option          "Device"        "/dev/input/evtouch_event-2500"
        Option          "DeviceName"    "Elo TouchSystems"
	Option		"AlwaysCore"
	Option		"Calibration"	"4091 -4104 4012 -78" #2500U model
        Option          "ReportingMode" "Raw"
EndSection

Section "InputDevice"
        Identifier      "touchscreen-2700"
        Driver          "evdev"
        Option          "Device"        "/dev/input/evtouch_event-2700"
        Option          "DeviceName"    "Elo TouchSystems"
        Option		"AlwaysCore"
        Option          "Calibration"   "4104 -3967 46 4043" #2700 model
        Option          "ReportingMode" "Raw"
EndSection

Section "Device"
        Identifier  "Card0"
        BusID       "PCI:0:2:0"
	Screen 0
EndSection

Section "Device"
        Identifier  "Card1"
        BusID       "PCI:0:2:0"
	Screen 1
EndSection

Section "Monitor"
        Identifier      "VGA1"
EndSection

Section "Monitor"
        Identifier      "DP2"
EndSection

Section "Screen"
        Identifier      "DefaultScreen"
        Monitor         "VGA1"
        Device          "Card0"
	SubSection	"Display"
		Viewport 0 0
		Depth	24
		Modes	"1024x768"
	EndSubSection

EndSection

Section "Screen"
        Identifier      "TopScreen"
        Monitor         "DP2"
        Device          "Card1"
	SubSection	"Display"
		Viewport 0 0
		Depth	24
		Modes	"1024x768"
	EndSubSection
EndSection

```

---

### Post by gordintoronto on 2012-09-07
I'm sorry this doesn't answer your question, but it might be relevant. Ubuntu 10.10 is no longer getting updates, so it is time to move to a more recent version: Ununtu 12.04, Xubuntu 12.04, Kubuntu 12.04 or Mint 13.

You will get a much more recent kernel by making this change, and it will probably affect your screensaver situation.

If memory serves, Ubuntu 12.04 doesn't even include a screensaver at installation.

---

### Post by dustinr on 2012-09-10
Upgrading really is not an option for me.

I did run across a couple things, but I have not been able to get them to work for me. On thing is Zaphod, I read that if i put ZaphodHeads inside of xorg.conf under the Device entry that it will let me have separate x displays ( :0.0 & :0.1 ). But when I look in the log it says that "Option "ZaphodHeads" is not used"...

So this led me to a gl-screensaver hack that can play two different screensavers on two different screens. I am hoping I can modify the source so one screen wont play a screen saver. In my attempts at doing this, I ran into compiling issues. The patch was successfully applied but I can not compile the source code.

I really seem to be banging my head against this, and ideas?

---

### Post by gordintoronto on 2012-09-10
> **dustinr said:**
> Upgrading really is not an option for me.
....
I really seem to be banging my head against this, and ideas?

What is the problem with upgrading?

You are frustrated that you can't solve this, others are frustrated that you don't apply the solution.

---

### Post by dustinr on 2012-09-11
Thanks for the tip, I am in the process of upgrading right now. I was hesitant because I didnt like the idea of upgrading the entire distribution for this. Hopefully it will work.

I found out that the xserver-xorg-video-intel that I am using for the i915 graphics I have, does NOT support separate x screens like the older i810 driver does.

---

### Post by dustinr on 2012-09-12
Ok, I just upgraded to 12.04.1 LTS and I am having the exact same result with my two screens. Perhaps I did not describe clearly what I am wanting. 

I think that the only way I can get my screensaver to only play on one of my screens and NOT the other ( that screen should never have any screensaver on it ) is to set up two separate x displays. This means that one screen will be :0.0 and the other will be :0.1 ( both will be on vt7 ). This will produce the result that some people do not like, that is I will not be able to move a windows from one screen to the other, this is fine for me.

I am using the intel i915 sandy bridge graphics controller with the "xserver-xorg-video-intel" driver, and I am now running ubuntu 12.04.1 LTS. 

Are there any kernel parameters I can pass or a command to run at start up? Currently I am editing xorg.conf in attempt to achieve my goal, but with no luck.

Thanks

---

