---
title: "Turn off touchpad when mouse is plugged in...automatically?"
date: 2006-06-15
forum: General Help
---

### Post by Lunar_Lamp on 2006-06-15
I have set up my laptop so that a simple press of ctrl+F5 toggles the touchpad on and off (so I don't knock it whilst typing, and because I use a mouse much of the time).  This was done according to the guide found [HERE]("https://wiki.ubuntu.com/SynapticsTouchpadHowTo?highlight=%28touchpad%29%7C%28synaptic%29#head-915292c9a5db68bef0ebd0f0362a206b5034adc3")

I was however thinking about taking this one step further by running a script that worked along these lines:

```
#!/bin/bash

OUTPUT=$(lsusb)

	if [ "OUTPUT" = "*Logic3 / SpectraVideo plc*" ]; then 	#this is what my mouse reads as
		synclient touchpadoff=1 			#typing this in turns the touchpad off
		wait 2 						#is 2 seconds a good time frame?
		go to start of script 	

	else synclient touchpadoff=0				#turns the touchpad on
		wait 2
		go to start of script


```

Problem number 1 is that I obviously don't know how to do loops (I'm exceptionally new to bash scripting).
Additonally, I don't know if this would take up too many system resources, though my initial reaction is that it wouldn't.
The input doesn't mind if the command "turn off" is entered when the touchpad is already turned off, though it would of course be nice not to keep sending the signal every 2 seconds if it's not needed.

---

### Post by pencilcheck on 2008-01-28
Well, does that work for you?
:confused:

---

### Post by Lunar_Lamp on 2008-01-28
No, that was never intended as a working script, and it's definitely not the way things should be done. If you're looking for a solution to this problem, you most likely want to look elsewhere.  You might be interested in SHMConfig (if I recall correctly) if you're just wanting to stop knocking the touchpad with your wrist when you're typing.

---

### Post by heindsight on 2008-01-28
It should be possible to do this with udev rules. Perhaps something like:
```
ENV{ID_CLASS}="mouse", ACTION=="add", RUN+="synclient touchpadoff=1"
ENV{ID_CLASS}="mouse", ACTION=="remove", RUN+="synclient touchpadoff=0"
```
in /etc/udev/rules.d/99-mouse.rules might do the trick. You'd probably need something
a bit more sophisticated than just ENV{ID_CLASS}="mouse" though (otherwise these rules might be triggered when the touchpad is detected at boot)

---

### Post by Lunar_Lamp on 2008-01-28
Yes, that's a far superior solution to the one I suggested 18months ago, heh.

---

### Post by steveneddy on 2008-01-28
Talk about waking up old threads.

---

### Post by cyberdonaldson on 2008-05-29
> **heindsight said:**
> It should be possible to do this with udev rules. Perhaps something like:
```
ENV{ID_CLASS}="mouse", ACTION=="add", RUN+="synclient touchpadoff=1"
ENV{ID_CLASS}="mouse", ACTION=="remove", RUN+="synclient touchpadoff=0"
```
in /etc/udev/rules.d/99-mouse.rules might do the trick. You'd probably need something
a bit more sophisticated than just ENV{ID_CLASS}="mouse" though (otherwise these rules might be triggered when the touchpad is detected at boot)

This idea worked great for me!  With some tinkering, I came up with this...
```
KERNELS=="4-1", SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{manufacturer}=="Logitech", ATTRS{product}=="USB Receiver", ACTION=="add", RUN+="/usr/bin/synclient touchpadoff=1"
KERNELS=="4-1", SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{manufacturer}=="Logitech", ATTRS{product}=="USB Receiver", ACTION=="remove", RUN+="/usr/bin/synclient touchpadoff=0"
```
... of course this is specifically for my cordless Logitech mouse, but it works great.  Just plug in the usb receiver and my touchpad turns off.

Thanks!

---

