---
title: "Help needed with Flex Design Tablet (Driver issue?)"
date: 2011-05-05
forum: General Help
---

### Post by JugglinPhil on 2011-05-05
Hi everybody,
I just purchased a Trust "[Flex Design Tablet]("http://www.trust.com/products/product.aspx?artnr=16937")" and I am trying to set it up under Natty.
I have the following problem: The tablet works for a few seconds, then does not respond any more until you hit the pen on it rather hard, after which it is back to working for a few seconds. This goes on endlessly, which leaves the whole thing rather useless.
I tried it on Windows 7 and it worked fine, so it looks like a driver issue. I tried the tutorial from [this thread]("http://ubuntuforums.org/showthread.php?t=1475433"), however it does not help much with my problem.
Any ideas on this?
Thanks in advance, 
JP

---

### Post by Favux on 2011-05-06
Hi JugglinPhil,

I don't recognize that tablet.  Is it a new product from Trust?  Is it bluetooth or usb?

Let's find out if the system sees it.  Enter in a terminal:
```
xinput list
```
and post the output.  Also try:
```
lsusb
```
and post the tablet line if it shows up.

---

### Post by JugglinPhil on 2011-05-06
Thanks for the reply, yes the system does see it.

xinput:

```
&#9116;   &#8627;          WALTOP             Tablet          id=10    [slave  pointer  (2)]

```lsusb:

```
Bus 007 Device 002: ID 172f:0037 Waltop International Corp. 

```

Since I just bought it from the store yesterday without any planning ahead I'm afraid I do not know whether it is new or not. It connects via USB.

---

### Post by Favux on 2011-05-06
OK, so it is a rebranded Waltop tablet.  That should be on the Wacom X driver in Natty.  Let's do a quick check and see if it is:
```
xinput list-props "WALTOP Tablet"
```
Please post the output.  My guess is it's on the evdev driver because the usb snippet in the 50-wacom.conf in Natty doesn't look like it has been updated.  Mine is reading:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM|Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
It should read:
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM|WALTOP|Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
Then restart.  You can use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
to edit the usb snippet.

It looks like I need to add Natty to the [Waltop HOW TO]("http://ubuntuforums.org/showthread.php?t=1595648").

---

### Post by JugglinPhil on 2011-05-07
xinput list-props:


```
Device '         WALTOP             Tablet    ':
    Device Enabled (147):    1
    Coordinate Transformation Matrix (149):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (269):    1.000000
    Device Accel Velocity Scaling (270):    10.000000
    Evdev Axis Inversion (539):    0, 0
    Evdev Axis Calibration (540):    <no items>
    Evdev Axes Swap (541):    0
    Axis Labels (542):    "Abs X" (536), "Abs Y" (537), "Abs Pressure" (538)
    Button Labels (543):    "Button Left" (150), "Button Middle" (151), "Button Right" (152), "Button Wheel Up" (153), "Button Wheel Down" (154), "Button Horiz Wheel Left" (155), "Button Horiz Wheel Right" (156), "Button Side" (534), "Button Extra" (535), "Button Unknown" (532), "Button Unknown" (532), "Button Unknown" (532), "Button Unknown" (532)
    Evdev Middle Button Emulation (544):    0
    Evdev Middle Button Timeout (545):    50
    Evdev Wheel Emulation (546):    0
    Evdev Wheel Emulation Axes (547):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (548):    10
    Evdev Wheel Emulation Timeout (549):    200
    Evdev Wheel Emulation Button (550):    4
    Evdev Drag Lock Buttons (551):    0


```I changed the file, restarting now.


EDIT: I modified the 50-wacom.conf file to your suggestions and restarted, but the problem is still there.
Have you got any more ideas? You really seem to know your stuff, glad you found my thread! :)

EDIT 2: Just for the record, to make the xinput list-props command work you need to quote the id-number instead of the actual name to make it work (in this case 10), i.e. 

```
xinput list-props "10"
```

---

### Post by Favux on 2011-05-07
Interesting.  The device name in quotes should work.  Maybe the big space between WALTOP and Tablet matters?  Anyway you can see that list-props is showing the tablet is on the evdev X driver, not the Wacom X driver.  Also with the ID # you don't need the quotes.  The problem with using the ID # is it can change when you hotplug the tablet or something else.

I checked the source code, wcmUSB.c in xf86-input-wacom and your product ID is in there.  From lsusb we know your Vendor ID = 172f = Waltop.  And your Product ID = 0037.  And in the table in wcmUSB.c I see:
```
	{ WALTOP_VENDOR_ID, 0x37,  80000,  80000, &usbGraphire4  },
```
So that's not the problem.

That would seem to indicate a problem with the match in the 50-wacom.conf usb snippet.  So is it the keyword or something else?  You'd think WALTOP would give the correct match despite the weird space and Tablet being there too.  So let's give this a shot:
```
Section "InputClass"
	Identifier "Wacom class"
#	MatchProduct "Wacom|WACOM|WALTOP|Hanwang"
	MatchVendor "WALTOP"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
and restart.

---

### Post by JugglinPhil on 2011-05-08
No, I'm afraid that did not work either. 
Just wondering, is it not possible that the driver simply does not work under Linux?
I got a CD with the Windows driver on it with the whole thing, would that be any use?

---

### Post by JugglinPhil on 2011-05-10
bump

---

### Post by Favux on 2011-05-10
Hi JugglinPhil,

That's not how it works.  There is a kernel driver in the usb hid (human interface device) section of the linux kernel for Waltop tablets.  The version in the 2.6.35 kernel (Maverick) pretty much worked with the linuxwacom X driver.  Now with Nikolai Kondrashov's patches the 2.6.38 kernel version it should work perfectly with the wacom X driver xf86-input-wacom.  The kernel driver is the usb part and it feeds data to the X windowing system driver or X driver.

So it should be working.  The likely problem is we're not get the matching right still.  It is probably still on the evdev X driver.  Let's take a look at what your Xorg.0.log is saying.  That's in /var/log.  Since it is big you can compress it by right clicking on it and using Create Archive.  Then attach it to your next post with Manage Attachments below.

Also make sure you have xf86-input-wacom installed.  It should be by default but check in Synaptic Package Manager or the Software Center to be sure.  Search 'wacom'.  The package it is in is called xserver-xorg-input-wacom.

---

### Post by JugglinPhil on 2011-05-11
Hi Favux,
thanks for the info, I think I sort of understand it. :D
I compressed the file (it was not that big..), here it is. 
Xserver-xorg-input-wacom is installed, as you said it was there by default.
Yours,
JP

---

### Post by Favux on 2011-05-11
Hmm.  The tablet doesn't seem to be in that Xorg.0.log.  It should be because it showed up in the *xinput list*.  Did you not have the tablet plugged in for that Xorg.0.log?  Or have you made some major change to your system?

---

### Post by JugglinPhil on 2011-05-11
Sorry, no I did not have it plugged in. ^^
Here we go again, should be fine now.

---

### Post by Favux on 2011-05-12
Hi JugglinPhil,

Well that actually looks OK:
```
[ 28169.790] (II) config/udev: Adding input device          WALTOP             Tablet     (/dev/input/event11)
[ 28169.790] (**)          WALTOP             Tablet    : Applying InputClass "evdev pointer catchall"
[ 28169.790] (**)          WALTOP             Tablet    : Applying InputClass "evdev tablet catchall"
[ 28169.790] (**)          WALTOP             Tablet    : Applying InputClass "Wacom class"
[ 28169.790] (II) LoadModule: "wacom"
[ 28169.850] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 28169.859] (II) Module wacom: vendor="X.Org Foundation"
[ 28169.859] 	compiled for 1.10.0, module version = 0.10.11
[ 28169.859] 	Module class: X.Org XInput Driver
[ 28169.859] 	ABI class: X.Org XInput driver, version 12.3
[ 28169.859] (II) Using input driver 'wacom' for '         WALTOP             Tablet    '
[ 28169.859] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 28169.859] (**)          WALTOP             Tablet    : always reports core events
[ 28169.859] (**) Option "Device" "/dev/input/event11"
[ 28169.860] (II)          WALTOP             Tablet    : type not specified, assuming 'stylus'.
[ 28169.860] (II)          WALTOP             Tablet    : other types will be automatically added.
[ 28169.860] (--)          WALTOP             Tablet     stylus: using pressure threshold of 27 for button 1
[ 28169.860] (--)          WALTOP             Tablet     stylus: Wacom USB Graphire4 tablet maxX=12288 maxY=9216 maxZ=1023 resX=80000 resY=80000  tilt=disabled
[ 28169.860] (II)          WALTOP             Tablet     stylus: hotplugging dependent devices.
[ 28169.860] (**)          WALTOP             Tablet     eraser: Applying InputClass "evdev pointer catchall"
[ 28169.860] (**)          WALTOP             Tablet     eraser: Applying InputClass "evdev tablet catchall"
[ 28169.860] (**)          WALTOP             Tablet     eraser: Applying InputClass "Wacom class"
[ 28169.860] (II) Using input driver 'wacom' for '         WALTOP             Tablet     eraser'
[ 28169.860] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 28169.860] (**)          WALTOP             Tablet     eraser: always reports core events
[ 28169.860] (**) Option "Device" "/dev/input/event11"
[ 28169.860] (--)          WALTOP             Tablet     eraser: Wacom USB Graphire4 tablet maxX=12288 maxY=9216 maxZ=1023 resX=80000 resY=80000  tilt=disabled
[ 28169.868] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input11/event11"
[ 28169.868] (II) XINPUT: Adding extended input device "         WALTOP             Tablet     eraser" (type: ERASER)
[ 28169.869] (--)          WALTOP             Tablet     eraser: top X=0 top Y=0 bottom X=12288 bottom Y=9216 resol X=80000 resol Y=80000
[ 28169.869] (**)          WALTOP             Tablet     eraser: (accel) keeping acceleration scheme 1
[ 28169.869] (**)          WALTOP             Tablet     eraser: (accel) acceleration profile 0
[ 28169.869] (**)          WALTOP             Tablet     eraser: (accel) acceleration factor: 2.000
[ 28169.869] (**)          WALTOP             Tablet     eraser: (accel) acceleration threshold: 4
[ 28169.876] (**)          WALTOP             Tablet     pad: Applying InputClass "evdev pointer catchall"
[ 28169.876] (**)          WALTOP             Tablet     pad: Applying InputClass "evdev tablet catchall"
[ 28169.876] (**)          WALTOP             Tablet     pad: Applying InputClass "Wacom class"
[ 28169.876] (II) Using input driver 'wacom' for '         WALTOP             Tablet     pad'
[ 28169.876] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 28169.876] (**)          WALTOP             Tablet     pad: always reports core events
[ 28169.876] (**) Option "Device" "/dev/input/event11"
[ 28169.880] (--)          WALTOP             Tablet     pad: Wacom USB Graphire4 tablet maxX=12288 maxY=9216 maxZ=1023 resX=80000 resY=80000  tilt=disabled
[ 28169.880] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input11/event11"
[ 28169.880] (II) XINPUT: Adding extended input device "         WALTOP             Tablet     pad" (type: PAD)
[ 28169.881] (**)          WALTOP             Tablet     pad: (accel) keeping acceleration scheme 1
[ 28169.881] (**)          WALTOP             Tablet     pad: (accel) acceleration profile 0
[ 28169.881] (**)          WALTOP             Tablet     pad: (accel) acceleration factor: 2.000
[ 28169.881] (**)          WALTOP             Tablet     pad: (accel) acceleration threshold: 4
[ 28169.881] (II)          WALTOP             Tablet     stylus: hotplugging completed.
[ 28169.884] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input11/event11"
[ 28169.884] (II) XINPUT: Adding extended input device "         WALTOP             Tablet     stylus" (type: STYLUS)
[ 28169.884] (--)          WALTOP             Tablet     stylus: top X=0 top Y=0 bottom X=12288 bottom Y=9216 resol X=80000 resol Y=80000
[ 28169.884] (**)          WALTOP             Tablet     stylus: (accel) keeping acceleration scheme 1
[ 28169.884] (**)          WALTOP             Tablet     stylus: (accel) acceleration profile 0
[ 28169.885] (**)          WALTOP             Tablet     stylus: (accel) acceleration factor: 2.000
[ 28169.885] (**)          WALTOP             Tablet     stylus: (accel) acceleration threshold: 4
[ 28169.886] (II) config/udev: Adding input device          WALTOP             Tablet     (/dev/input/mouse1)
[ 28169.886] (II) No input driver/identifier specified (ignoring)
```
We're interested in the stylus lines:
```
[ 28169.859] (II) Using input driver 'wacom' for '         WALTOP             Tablet    '
[ 28169.859] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 28169.859] (**)          WALTOP             Tablet    : always reports core events
[ 28169.859] (**) Option "Device" "/dev/input/event11"
[ 28169.860] (II)          WALTOP             Tablet    : type not specified, assuming 'stylus'.
[ 28169.860] (II)          WALTOP             Tablet    : other types will be automatically added.
[ 28169.860] (--)          WALTOP             Tablet     stylus: using pressure threshold of 27 for button 1
[ 28169.860] (--)          WALTOP             Tablet     stylus: Wacom USB Graphire4 tablet maxX=12288 maxY=9216 maxZ=1023 resX=80000 resY=80000  tilt=disabled
......
[ 28169.884] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input11/event11"
[ 28169.884] (II) XINPUT: Adding extended input device "         WALTOP             Tablet     stylus" (type: STYLUS)
[ 28169.884] (--)          WALTOP             Tablet     stylus: top X=0 top Y=0 bottom X=12288 bottom Y=9216 resol X=80000 resol Y=80000
[ 28169.884] (**)          WALTOP             Tablet     stylus: (accel) keeping acceleration scheme 1
[ 28169.884] (**)          WALTOP             Tablet     stylus: (accel) acceleration profile 0
[ 28169.885] (**)          WALTOP             Tablet     stylus: (accel) acceleration factor: 2.000
[ 28169.885] (**)          WALTOP             Tablet     stylus: (accel) acceleration threshold: 4
```
Notice the weird format of the "device name":
```
"         WALTOP             Tablet     stylus"
```
That I don't really understand.  Looks like a formatting error, maybe in the tablet firmware?

This line means:
```
[ 28169.884] (II) XINPUT: Adding extended input device "         WALTOP             Tablet     stylus" (type: STYLUS)
```
the tablet should be showing up in *xinput list* and it should be on the wacom driver in *list-props*.  Have you checked?  If you're seeing the wacom driver in *list-props* do you see the stylus in the:
```
xsetwacom list
```
output?

---

### Post by JugglinPhil on 2011-05-12
Hi Favux, 
thanks once again for your explanations an time. 
The stylus does show up, it even lists an eraser (never knew tablets had an extra eraser-do you know how to use it?).
Anyway, for some reason I think it is slowly getting better, the crashes are getting rarer and I can actually (sort of) draw something.
Is this even possible or is that just my wishful imagination?

---

### Post by Favux on 2011-05-12
No, that's possible.  Sometimes it takes several reboots for things to shake out.  That's not suppose to happen but it does.

The eraser is probably spurious because I haven't encountered a Waltop with one yet.  It would be on the stylus at the opposite end from the tip.  Looks sort of like eraser and kinda depresses a little into the barrel of the stylus.  I think that's coming because they paired the Waltop tablets with similar Wacom tablets, in your case the Wacom USB Graphire4 tablet.

---

### Post by JugglinPhil on 2011-05-13
Okay that makes sense, so would you suggest marking it as solved?

Thanks for the eraser-info, it does have such a thing at the back of it however it does not seem to do anything. But whatever, that's the last thing I'll worry about. :)

---

### Post by Favux on 2011-05-13
Sure, if you feel your issues are solved go ahead and mark the thread as Solved.

Now that's interesting, maybe your Waltop stylus does have an eraser.  The eraser will work in certain programs that support it like Gimp, Inkscape, and Xournal if you enable it.  In Gimp and Inkscape you enable the extended input devices.  See the screen shots near the bottom of the Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

