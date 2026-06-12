---
title: "Touchpad Control Synaptic"
date: 2006-02-21
forum: General Help
---

### Post by powdercarrot on 2006-02-21
Adjusting the sensitivity on my synaptic touchpad (HP dv1000 notebook) has no effect in Breezy. How can I get this thing to move less than five feet when I move my finger 2mm?

---

### Post by schilcha on 2006-02-22
Do you have the synaptics-driver installed (package "xorg-driver-synaptics")? If so, is it included in your xorg-configuration?

I recently fiddled around with /etc/X11/xorg.conf and removed the synaptics-related sections. The result was a tremendously quickly moving mouse pointer. Here's the stuff that slows my pointer down to reasonable speed:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

[...]

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

[...]

```

If you have all that, look at "synclient". According to the docs, you can use it to adjust the behaviour of your synaptic-touchpad. It's installed allong with the "xorg-driver-synaptics"-package. However, I've never used it...

Good Luck!

---

### Post by nrwilk on 2006-02-22
Did you try a ceremony in which you sacrificed a chicken?

[http://ubuntuforums.org/showthread.php?t=132157](http://ubuntuforums.org/showthread.php?t=132157)

Sorry, I just love the title of that thread.

---

### Post by beartard on 2006-02-22
Here's my xorg.conf synaptics configuration.  I copied it from somewhere online and haven't had any trouble at all.  Give it a go.  As always, make a backup of your xorg.conf before editing anything.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/event2"
	Option		"Protocol"		"event"
	Option		"LeftEdge"		"120"
        Option		"RightEdge"		"830"
        Option		"TopEdge"		"120"
        Option		"BottomEdge"		"650"
        Option		"FingerLow"		"14"
        Option		"FingerHigh"		"15"
        Option		"MaxTapTime"		"180"
        Option		"MaxTapMove"		"110"
        Option		"ClickTime"		"0"
        Option		"EmulateMidButtonTime"	"75"
        Option		"VertScrollDelta"	"10"
        Option		"HorizScrollDelta"	"0"
        Option		"MinSpeed"		"0.45"
        Option		"MaxSpeed"		"0.75"
        Option		"AccelFactor"		"0.020"
        Option		"EdgeMotionMinSpeed"	"200"
        Option		"EdgeMotionMaxSpeed"	"200"
        Option		"UpDownScrolling"	"1"
        Option		"CircularScrolling"	"0"
        Option		"CircScrollDelta"	"0.1"
        Option		"CircScrollTrigger"	"2"
        Option		"SHMConfig"		"true"
EndSection

```

---

### Post by powdercarrot on 2006-02-23
I accidentally deleted the display section of my xorg.conf file.  What is the best way to recover?  I have an HP dv1000 laptop.  How do I navigate to the x11 directory to edit with nano?

---

### Post by nik on 2006-02-23
sudo nano /etc/X11/xorg.conf

But you could try to reconfigure your xserver. Something like

sudo dpkg-reconfigure xserver-xorg

---

