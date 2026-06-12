---
title: "TM2t 2100 CTO - Wacom - pen - right click"
date: 2011-03-14
forum: General Help
---

### Post by tembares on 2011-03-14
Hello all,
Thank you for reading.
Everywhere I read the right click on the pen works out of the box.
I am looking for a solution for 2 days now and finally I am posting my question:
Who can help me to get the right button on the pen to work?
Maybe these files are the cause. They came out of /usr/share/X11/xorg.conf.d

**50-two-finger-scroll-touchsmart-tm2.conf**
Section "InputClass"
   Identifier "enable synaptics SHMConfig" 
   MatchIsTouchpad "on"  
   MatchDevicePath "/dev/input/event*"
   Driver "synaptics"
   Option "SHMConfig" "on"
   Option "EmulateTwoFingerMinW" "5"
   Option "EmulateTwoFingerMinZ" "60"
   Option "VertTwoFingerScroll" "1"
   Option "HorizTwoFingerScroll" "1"
EndSection

**50-wacom.conf**
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "TPCButton" "on"
	Option "Button2" "3"
EndSection

**50-synaptics.conf**
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
EndSection

**51-synaptics-quirks.conf**
Section "InputClass"
	Identifier "Dell Inspiron embedded buttons quirks"
	MatchTag "inspiron_1011|inspiron_1012"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "90"
	Option "AreaBottomEdge" "4100"
EndSection

Section "InputClass"
	Identifier "Dell Inspiron quirks"
	MatchTag "inspiron_1120"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "250"
EndSection

Section "InputClass"
	Identifier "HP Mininote quirks"
	MatchTag "mininote_1000"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "20"
EndSection

**60-magictrackpad.conf**
Section "InputClass"
         Identifier "Magic Trackpad"
         MatchUSBID "05ac:030e"
         Driver "evdev"
EndSection

---

### Post by Favux on 2011-03-14
Hi tembares,

It should work out of the box in Maverick.  How many side buttons does your stylus have?  Two?

To find out what setting the button currently has enter *xinput list* in a terminal and then determine the "device name" for the stylus and using that with quotes enter:
```

xsetwacom get "device name" Button2

xsetwacom get "device name" Button3
```

Where did the 50-two-finger-scroll-touchsmart-tm2.conf come from?  Did you add it?  Why not use the gestures in the Wacom driver?

---

### Post by tembares on 2011-03-15
Thank you for your answer.
I found the two-finger-file somewhere on the internet, hoping to make the input better. Do you recommend to remove it?

I will search about gestures, because I do not know what that is.

The output xinput list:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Finger touch             	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen eraser               	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen stylus               	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]

This doesn't say to me anything, you?

Thank you in advance

---

### Post by Favux on 2011-03-15
Now you use the "device name":
```
xsetwacom get "Wacom ISDv4 E3 Pen stylus" Button2

```
It would also be useful to verify what driver the input devices are on:
```

xinput list-props "Wacom ISDv4 E3 Pen stylus"
and
xinput list-props "Wacom ISDv4 E3 Finger touch"
```

---

### Post by tembares on 2011-03-15
Thank you again for your quick reply.
Further browsing and looking for more information about the command's you gave me I found the following that worked for me:
**50-wacom.conf**

Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button2" "2"
        Option "Button3" "3"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Now I have to find how to get the eraser to work and search what gestures are (English is not my native language).

Thank you!

---

### Post by Favux on 2011-03-15
Nice work!

The eraser only works in programs that support it.  In Gimp and Inkscape or Xournal you have to configure it.  With Gimp and Inkscape in the extended input devices.  See the screen shots near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

Two finger gestures for the linuxwacom drivers are:
One finger double click - left click
Two finger doulbe click - right click (one finger down, then bring the second finger down)
Two finger horizontal and vertical scroll
Pinch zoom

---

### Post by vedovatti on 2011-03-26
Hi guys,

I would really like ask you for support.

I have the same problem and configuration as tembares. xinput list is the same and I tried both solutions to change the whole 50-wacom file to the last posted. Didn't work for me. I tried the solution: xsetwacom get "Wacom ISDv4 E3 Pen stylus" Button2. Nether that one.

I have the same computer HP touchsmart tm2 and the same pen 1 button. The erase works perfectly as well pen but the button to have the right click, doesn't work. No action at all!

Any suggestion. It is important because this computer the touchpad is completely bad configured. So to have the pen working would be really great.

Thanks guys

---

### Post by Favux on 2011-03-26
Hi vedovatti,

Are you in Lucid or Maverick?

> xsetwacom get "Wacom ISDv4 E3 Pen stylus" Button2
Determines the value it is currently set to.  You have to use a *set* command to change the setting.

What do see with the following in a terminal:
```
xsetwacom list
```
Do you have the default linux drivers for your release or did you change them?

---

### Post by vedovatti on 2011-03-27
Thank you for your fast reply!

I am using Maverick and the default drivers. 

In the desperate try, I installed yesterday wacom-dkms from the utouch ppa team to activate multitouch. But no effect at all. So I will erase it!

Beside that I have the same config as Tamberes post #1 beside the "50-two-finger-scroll-touchsmart-tm2.conf". It was a workarround that everybody reccomend for this computer but I tried and didnt work at all. So I installed from the utouch ppa team the touchpad dkms and help a little bit. Without the touchpad dkms, the touchpad (is a 7.4 by the way) is useless, now is the buttons are not correct configured but at least i can half use it.

Ok, so with the xsetwacom list I get this:
> Wacom ISDv4 E3 Finger touch TOUCH     
Wacom ISDv4 E3 Pen eraser ERASER    
Wacom ISDv4 E3 Pen stylus STYLUS
And with the commands: xsetwacom get "Wacom ISDv4 E3 Pen stylus" Button2
I get:
> 2
and with: "xsetwacom get "Wacom ISDv4 E3 Pen stylus" Button3"
I get:
> 3
What do you recommend?

Thanks

---

### Post by vedovatti on 2011-03-27
Hi there,

I solve the problem. I mean I know how it works now.

The button works great. The fact it is that it activates the right-click only if the pen is touching the screen. In windows the right-click works even if you are not touching the screen but when the screen detects the pen near without touching it.

So, I am sorry I think its all right now! I works out of the box. Just a different way to use it. I just hope the touchpad bug will be solve in future.

Thanks again

---

### Post by Favux on 2011-03-27
Hi vedovatti,

In Windows you are describing the hover mode, which is the default for non-tablet PC graphics tablets.  For tablet PCs the default is:
```
xsetwacom set "device name" TabletPCButton on
```
To get it to work like in Windows you would have to change it to off.  Unfortunately the TabletPCButton parameter was activated only recently and doesn't work in the default xf86-input-wacom-10.8 in Maverick.

Are you describing the Synaptic touch pad or the touch screen of your Wacom digitizer?  Because we should be able to get Wacom multi-touch working for you.

---

### Post by vedovatti on 2011-03-28
Thanks for your answer again!

So I tried:
```
xsetwacom set "Wacom ISDv4 E3 Pen stylus" TabletPCButton off
```
And I got:> Unknown parameter name 'TabletPCButton'.

About the multitouch, doesn't work in the touchpad and neither on the touchscreen. 

I already saw some bugs reported from the touchpad synaptics 7.2 and 7.4, so that means that I am not the only one with the problem. I have to say that I am lucky that it half works with the synaptics-dkms I installed. Let's hope it will be solve in future.

About the multitouch in the screen. You know how to solve it? I tried the multitouch with pictures in the program Eye of Gnome, doesn't work. Or does it work with just specific programs?

Cheers

---

### Post by Favux on 2011-03-28
Sorry I wasn't clear.  A lot of parameter names changed with xf86-input-wacom-0.10.11.  The version that is default in Maverick is 0.10.8.  So the parameter was called *TPCButton* in 0.10.8.  But as I said I don't think it actually works in 0.10.8, but worth trying I suppose.

> About the multitouch, doesn't work in the touchpad and neither on the touchscreen.
As far as I know the TM2 multi-touch works on the linux Wacom drivers.  The TM2 has two finger (2FG) multi-touch, correct?

You might want to update to a more recent version of xf86-input-wacom to get the latest touch features and bug fixes.  And also maybe update your wacom.ko.  First you probably would want to disable or remove your Synaptic driver setup.

Why are TM2's using the Synaptic driver?  Better performance, more gestures?  Or does the TM2 support more than 2 fingers?

The TM2 would have higher resolution than a standard touchpad.  So enabling the Synaptic driver for it would require a match and a change in the coordinate size.  That may be what is disabling the regular touchpad.  It would depend on the Synaptic driver and how the match is being made.  In other words is there a separate later .conf file for the TM2 and can the Synaptic driver handle being fed two separate dimensions for two separate devices?

---

### Post by vedovatti on 2011-03-31
Hi there,

I tried the command TPCButton, unfortunatelly didn't work. I tried to install the last release of the wacom driver version but I am missing dependencies. I think I prefer to wait until ubuntu 11.04 is released and give it a tried. I already destroyed the system so many times because of the installing drivers, probably because I am not an expert.

Anyway, about the multitouch infact it is a 2 fingers multitouch. 
The fact is that when you install ubuntu on this computer the touchpad doesnt work really well. It becomes hypersensitive, it moves to fast, cannot change features and when it detects two fingers on the pad the pointer goes crazy. With the dkms-synaptics it is stable just that the buttons doesnt work properly (the right button specially).

I think I will leave it like this. It's fine just hope that the 11.04 will work better these features.

Thank you very much!

---

