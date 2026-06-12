---
title: "wacom mouse issue in 10.04"
date: 2010-07-29
forum: General Help
---

### Post by tankjl on 2010-07-29
Hi all
[COLOR=black][FONT=Verdana]I just loaded unbuntu 10.04 on my laptop and sometimes when I boot the mouse on my wacom graphire4 tablet does not move smoothly, the action is "delayed" making for a rather jerky moment of the pointer. Its an older Toshiba with 1.5 gigs of memory and 1.6 Intel processor. Any way to fix this? Also sometimes when I unplug it then plug it back in unbuntu fails to recognize it.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thanks[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Jeff[/FONT][/COLOR]

---

### Post by Favux on 2010-07-29
Hi Jeff,

Welcome to Ubuntu forums!

Is there any particular program you're noticing the lag in?

Let's look at your output in a terminal of:
```
xinput --list
```
We can also look at your Xorg.0.log in /var/log.  Go ahead and attach it to your next post.

---

### Post by tankjl on 2010-07-29
the lag is in the X-windows system any program and just the desktop in general, using gnome.

the output of 

rocketman@old-top:/var/log$  xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 eraser                  id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 cursor                  id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 pad                     id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5                         id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

the output of the log file showing the wacom section pasted below

(II) config/udev: Adding input device Wacom Graphire4 4x5 (/dev/input/event5)
(**) Wacom Graphire4 4x5: Applying InputClass "evdev tablet catchall"
(**) Wacom Graphire4 4x5: Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.10.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event5"
(II) Wacom Graphire4 4x5: type not specified, assuming 'stylus'.
(II) Wacom Graphire4 4x5: other types will be automatically added.
(**) Wacom Graphire4 4x5: always reports core events
(**) Option "KeepShape" "on"
(II) Wacom Graphire4 4x5: hotplugging dependent devices.
(**) Option "Device" "/dev/input/event5"
(**) Wacom Graphire4 4x5 eraser: always reports core events
(**) Option "KeepShape" "on"
(II) XINPUT: Adding extended input device "Wacom Graphire4 4x5 eraser" (type: ER
ASER)
(--) Wacom Graphire4 4x5 eraser: using pressure threshold of 30 for button 1
(--) Wacom Graphire4 4x5 eraser: Wacom USB Graphire4 tablet speed=38400 maxX=102
08 maxY=7424 maxZ=511 resX=2032 resY=2032  tilt=disabled
(--) Wacom Graphire4 4x5 eraser: top X=0 top Y=0 bottom X=10208 bottom Y=6380 re
sol X=2032 resol Y=2032
(**) Option "Device" "/dev/input/event5"
(**) Wacom Graphire4 4x5 cursor: always reports core events
(**) Option "KeepShape" "on"
(II) XINPUT: Adding extended input device "Wacom Graphire4 4x5 cursor" (type: CU
RSOR)
(--) Wacom Graphire4 4x5 cursor: top X=0 top Y=0 bottom X=10208 bottom Y=6380 re
sol X=2032 resol Y=2032
(**) Option "Device" "/dev/input/event5"
(**) Wacom Graphire4 4x5 pad: always reports core events
(**) Option "KeepShape" "on"
(II) XINPUT: Adding extended input device "Wacom Graphire4 4x5 pad" (type: PAD)
(--) Wacom Graphire4 4x5 pad: top X=0 top Y=0 bottom X=10208 bottom Y=6380 resol
 X=2032 resol Y=2032
(II) Wacom Graphire4 4x5: hotplugging completed.
(II) XINPUT: Adding extended input device "Wacom Graphire4 4x5" (type: STYLUS)
(--) Wacom Graphire4 4x5: top X=0 top Y=0 bottom X=10208 bottom Y=6380 resol X=2
032 resol Y=2032
(II) config/udev: Adding input device Wacom Graphire4 4x5 (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)

 this is from the logs on my last login where the tablet mouse and pen are responding just fine.
looking at the last log before that it reads the same and the last time I started up it was acting flaky.
hotplug option seems enabled from what I see in the logs.

Jeff

---

### Post by Favux on 2010-07-29
What's the CPU on the laptop (ie how old is it)?

We can try and block the spurious mouse* events in the 10-wacom.conf at /usr/lib/X11/xorg.conf.d/ and see if that makes a difference.  After the usb snippet and before the serial snippet add:
```
Section "InputClass"
	Identifier "Wacom ignore mouse dev"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/mouse*"
	Option "Ignore" "yes"
EndSection
```

---

### Post by tankjl on 2010-08-01
well it seems that when I plug the tablet into the USB hub I sometimes get the erratic movement but when I plug it in directly it seems to always work.
Now how can I get it to hotplug? i found info on the 10-wacom.fdi file but nothing about what it contains and there isn't any such file on my system in either of the 20thirdparty directories where it is supposed to be, if I understand how the hotpluging in Ubuntu works.

Thanks

Jeff

---

### Post by Favux on 2010-08-01
Hi Jeff,

There aren't .fdi files anymore in Lucid.  For hot plugging you have the 10-wacom.conf I mentioned above.  Usb hubs can be problematic.  I suggest plugging directly until you have everything worked out.

---

### Post by tankjl on 2010-08-01
thanks, that what I hought. I may have to try go to 9.10 since the tablet problems and intermittent disconnects from the wifi are real problems for me. plus I can't get the tablet stylus to respond to pressure making photo retouching nearly impossible. The tablet does not respond at all when plugged into the other two USB ports on my laptop. Perhaps once I get my new faster laptop with more memory this might be less of a problem since I will have enough disk space in the new system to store everything and then only need the outboard disk for backups.

Jeff

---

### Post by tankjl on 2010-08-02
issue resolved, got a new laptop!
 
Jeff

---

### Post by Favux on 2010-08-02
Lucky devil!

---

### Post by TheNerdAL on 2010-08-02
> **tankjl said:**
> issue resolved, got a new laptop!
 
Jeff

Give me the old one. :P

---

