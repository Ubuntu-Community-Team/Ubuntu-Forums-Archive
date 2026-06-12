---
title: "I hate the mouse!"
date: 2006-06-05
forum: General Help
---

### Post by android6011 on 2006-06-05
I have a laptop with touchpad mouse, however I hate how sensitive it is and the actions it performs. I turned the sensitivity way down, but that didnt help. When Im moving the mouse, and have to put my finger back on it to keep moving it grabs icons and such like I am trying to move them. I did not slam on the pad or anything, but it still grabs them. Also when trying to move a windows it is pretty much impossible because I click to move, but the when I touch the pad to direct the move it is sent behind other windows. Which brings me to the final thing which is how do I stop when I click the title bar of a window it getting sent behind other windows? Thanks

---

### Post by NiceGuy on 2006-06-05
Your best bet would be to edit your /etc/X11/xorg.conf file. Somewhere in there you will find the settings for your touchpad (you can define some pretty specifc settings if you can be bothered - and if you use your laptop a lot then you'll want to!. 

If you want an example here is what my touchpad section looks like. ```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
  	Option          "Device" "/dev/psaux"
  	Option		"Protocol"	"auto-dev"
  	Option		"LeftEdge"      "1700"
  	Option		"RightEdge"     "5300"
  	Option		"TopEdge"       "1700"
  	Option		"BottomEdge"    "4200"
  	Option		"FingerLow"	"25"
  	Option		"FingerHigh"	"30"
  	Option		"MaxTapTime"	"180"
  	Option		"MaxTapMove"	"220"
  	Option		"VertScrollDelta" "100"
    	Option         	"HorizScrollDelta" "100"
  	Option		"MinSpeed"	"0.09"
  	Option		"MaxSpeed"	"0.18"
  	Option		"AccelFactor"	"0.0015"
  	Option        	"PalmMinWidth" "70"
  	Option        	"PalmMinZ" "200"
  	Option		"SHMConfig"	"on"
EndSection
```

---

### Post by md4life on 2006-06-07
hi there, i'm running drake on my hp pavilion zv5000z laptop and i'm having the same problem with my touchapd.  the damn thing is hyper sensitive and trying to lower the sensitivity from the administaration panel doesn't help at all.  when i access the xorg.conf file, all the touchpad options in NiceGuy's post are missing.  does anyone know what's wrong?  any help would be much appreciated.

---

### Post by grsing on 2006-06-07
I think Ubuntu just has it set a lot higher, for no apparent reason.  I found that, once I got used to it, I actually usually like it better, though it takes time.  If you prefer it the way it is on Windows, editing xorg.conf like NiceGuy showed should do it (just make a backup copy and play around with the settings to find what you like).

---

### Post by NiceGuy on 2006-06-08
Its true that the options aren't there by default, you need to add them! :D

If anyone is interested I based my settings on the ones found at [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Synaptic_Xorg_Installation_and_Configuration]("http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Synaptic_Xorg_Installation_and_Configuration")

So if your looking for more info, I'd start there!

---

### Post by elamericano on 2006-06-08
Clicking to move a window behind is a middle button action on my computer. If you can get the taps to be left-clicks (look for two-button mouse emulation) then that might be what you need.

---

