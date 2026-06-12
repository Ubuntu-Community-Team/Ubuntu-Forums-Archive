---
title: "Aiptek Graphics Tablet in Oneiric"
date: 2011-12-03
forum: General Help
---

### Post by Henkdroid on 2011-12-03
I tried following the instructions in the community documentation but to no avail. Is there any way to get the Aiptek drivers to work on 11.10?

---

### Post by Favux on 2011-12-03
Hi Henkdroid,

Did you install xserver-xorg-input-aiptek through the Software Center or Synaptic Package Manager?

What is the tablet line in the output of?
```
lsusb
```
Also what is the output of this terminal command?
```
xinput list
```

---

### Post by Henkdroid on 2011-12-07
I installed it with Synaptic
```
Thinkpad:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 08ca:0010 Aiptek International, Inc. Tablet

```
```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Aiptek stylus                           	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Aiptek eraser                           	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Aiptek cursor                           	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]

```
Sorry for the late reply.

---

### Post by Favux on 2011-12-07
Alright, looks good so far.  But the stylus isn't working yet?

Do you have an aiptek.conf?  It should be in /usr/share/X11/xorg.conf.d.  Don't know the number, maybe 50?  If so could you post the contents and the number/name?

Also does your stylus have an eraser?  Do you have a tablet mouse (the cursor)?

---

### Post by Henkdroid on 2011-12-07
No eraser and the mouse squeaked off :(
I do have a 50-aiptek.conf
The tablet is a 12000U, rebranded as a Tevion.

---

### Post by Favux on 2011-12-07
OK, so we're just talking the stylus but there was a mouse.  The Aiptek X driver appears to be appending device type to the parent device it looks like from *xinput list*.  So given that device type (stylus etc.) is being appended it seems the 50-aiptek.conf is matching the tablet to the driver.  But let's be sure.  Please post the contents of the .conf and the output of:
```
xinput list-props "Aiptek stylus"
```

No reaction at all when you move the stylus?

---

### Post by Henkdroid on 2011-12-07
OK, when I checked the 50-aiptek.conf it didn't match the one in the community docs. I replaced it with the .conf in the docs. I restarted and inputted xinput list:
```
Thinkpad:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Aiptek                                  	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]

```
When I tried ```
xinput list-props "Aiptek stylus"
```
I got an error so I tried ```
xinput list-props "Aiptek"
```
and I got ```
Thinkpad:~$ xinput list-props "Aiptek"
Device 'Aiptek':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (256):	0
	Device Accel Constant Deceleration (257):	1.000000
	Device Accel Adaptive Deceleration (258):	1.000000
	Device Accel Velocity Scaling (259):	10.000000
	Device Node (255):	"/dev/input/event10"
	Wacom Tablet Area (554):	0, 0, 5999, 4499
	Wacom Rotation (555):	0
	Wacom Pressurecurve (556):	0, 0, 100, 100
	Wacom Serial IDs (557):	16, 0, 2, 0
	Wacom Serial ID binding (558):	0
	Wacom Pressure Threshold (559):	27
	Wacom Sample and Suppress (560):	2, 4
	Wacom Enable Touch (561):	1
	Wacom Hover Click (562):	1
	Wacom Enable Touch Gesture (563):	0
	Wacom Touch Gesture Parameters (564):	50, 20, 250
	Wacom Tool Type (565):	"STYLUS" (486)
	Wacom Button Actions (566):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Device Product ID (254):	2250, 16
	Wacom Debug Levels (567):	0, 0

```

---

### Post by Favux on 2011-12-07
Right, the "device name" changed so you need to use the current one with xinput.

Well list-props now says you now have the tablet on the Wacom X driver.  So likely there is a line saying *driver "wacom"* instead of *driver "aiptek"*.

Maybe third time is the charm.  Please post the contents of your community wiki aiptek.conf.  And I would still like to see the contents of your original aiptek.conf, which was presumambly installed by the xserver-xorg-input-aiptek package for Oneiric.

---

### Post by Henkdroid on 2011-12-07
The community one is:
```
Section "InputClass"
        Identifier "pen"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "SendCoreEvents" "true"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "511"
EndSection
```
and I don't know how to get the one from the package.

---

### Post by Favux on 2011-12-07
That's interesting.  How are you getting a match to the Wacom X driver with that?  It sure seems like it should be putting the tablet on the aiptek driver because the keyword for the match is correct.  We need to look at the Xorg.0.log in /var/log to see what's going on.

Go ahead in Synaptic Package Manager and tell it to reinstall the aiptek driver package.  That will get the other .conf reinstalled for you.

---

### Post by Henkdroid on 2011-12-07
I did a complete remove and an install then restarted X, I checked the .conf and it is still the same.
I looked in the log and skipped to the Aiptek bit:
```
[   743.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-89D0835B7D65837BCF1AA41FF54A5C5DF983ED35.xkm
[   835.765] (II) config/udev: Adding input device Aiptek (/dev/input/mouse2)
[   835.882] (II) No input driver/identifier specified (ignoring)
[   835.882] (II) config/udev: Adding input device Aiptek (/dev/input/event10)
[   835.882] (**) Aiptek: Applying InputClass "evdev pointer catchall"
[   835.882] (**) Aiptek: Applying InputClass "evdev keyboard catchall"
[   835.882] (**) Aiptek: Applying InputClass "evdev tablet catchall"
[   835.882] (**) Aiptek: Applying InputClass "pen"
[   835.882] (**) Aiptek: Applying InputClass "Wacom class"
[   835.882] (**) Aiptek: Applying InputClass "Waltop on wacom class"
[   835.892] (II) LoadModule: "wacom"
[   835.912] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   835.932] (II) Module wacom: vendor="X.Org Foundation"
[   835.932] 	compiled for 1.11.2, module version = 0.12.0
[   835.932] 	Module class: X.Org XInput Driver
[   835.932] 	ABI class: X.Org XInput driver, version 13.0
[   835.932] (II) Using input driver 'wacom' for 'Aiptek'
[   835.932] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   835.932] (**) Option "SendCoreEvents" "true"
[   835.932] (**) Aiptek: always reports core events
[   835.932] (**) Option "Device" "/dev/input/event10"
[   835.932] (**) Option "Type" "stylus"
[   835.932] (**) Option "Mode" "absolute"
[   835.933] (--) Aiptek: using pressure threshold of 27 for button 1
[   835.933] (--) Aiptek: Wacom Unknown USB tablet maxX=5999 maxY=4499 maxZ=511 resX=1016 resY=1016  tilt=enabled
[   835.936] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input10/event10"
[   835.936] (II) XINPUT: Adding extended input device "Aiptek" (type: STYLUS, id 13)
[   835.956] (**) Aiptek: (accel) keeping acceleration scheme 1
[   835.956] (**) Aiptek: (accel) acceleration profile 0
[   835.956] (**) Aiptek: (accel) acceleration factor: 2.000
[   835.956] (**) Aiptek: (accel) acceleration threshold: 4
```
It seems to be loading the wacom driver.

---

### Post by Favux on 2011-12-07
Notice how in the aiptek.conf you have the Identifier says pen.  That's so there is a human readable label in Xorg.0.log.  So looking at what's matching you see:
```
[   835.882] (**) Aiptek: Applying InputClass "evdev pointer catchall"
[   835.882] (**) Aiptek: Applying InputClass "evdev keyboard catchall"
[   835.882] (**) Aiptek: Applying InputClass "evdev tablet catchall"
[   835.882] (**) Aiptek: Applying InputClass "pen"
[   835.882] (**) Aiptek: Applying InputClass "Wacom class"
[   835.882] (**) Aiptek: Applying InputClass "Waltop on wacom class"
[   835.892] (II) LoadModule: "wacom"

```
The last one to match controls which is why the module wacom is loading.  That's because "Waltop on wacom class" told it to use the Wacom X driver for your tablet.

So you have two .confs you altered trying to get the aiptek to work.  Probably the 50-wacom.conf in /usr/share/X11/xorg.conf.d which is the "Wacom class".  Remove the Aiptek match from that and try to return it to the default state.  You need to do the same to the .conf that has the "Waltop on wacom class" Identifier, probably 52-waltop-on-wacom.conf in /etc/X11/xorg.conf.d, or remove it.

I'll see if I can figure out what the default aiptek.conf looks like.


Edit:  Looks like the Aiptek package still doesn't install a 50-aiptek.conf.  Haven't figured out yet if there is one in the package or not, but if there it isn't installed.  So the original must have been something you installed from the community wiki.  I'll bet you upgraded to Oneiric from say Natty.


Edit2:  Yep, no aiptek.conf in the package.  How 'bout that.  That's getting to be silly.  OK, they forget it in Natty, but again in Oneiric?

---

