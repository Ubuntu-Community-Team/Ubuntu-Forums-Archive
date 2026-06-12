---
title: "Bluetooth Mouse Speed"
date: 2011-10-20
forum: General Help
---

### Post by Quarkrad on 2011-10-20
Newbie. Installed bluetooth mouse on 11.10 - worked 'out of the box'.  However, mouse speed too fast despite setting gui to lowest speed.  Is there any way of 'getting under the bonnet' to configure/adjust the mouse speed?

---

### Post by mikejonesey on 2011-10-20
[http://www.mikejonesey.co.uk/articles/pci-and-xinput-device-checker-scripts.html](http://www.mikejonesey.co.uk/articles/pci-and-xinput-device-checker-scripts.html)

try the xinput checker

```
./xinput-checker.sh ps/2
```

this will list all availible properties for your mouse and their current settings...

---

### Post by Quarkrad on 2011-10-21
Mike - success.  I have an output but not sure what to do now re changing the mouse speed.  Any advice - note I'm a newbie to linux/terminal commands.

[B]mimi@mimiubuntu:~$ ./xinput-checker.sh ps/2
-------- device -------- 
PS/2 Logitech Mouse                     	id=10	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 10
		Buttons supported: 5
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 10
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 10
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative

-------- device props -------- 
Device 'PS/2 Logitech Mouse':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (241):	0
	Device Accel Constant Deceleration (242):	1.000000
	Device Accel Adaptive Deceleration (243):	1.000000
	Device Accel Velocity Scaling (244):	10.000000
	Evdev Axis Inversion (245):	0, 0
	Evdev Axes Swap (247):	0
	Axis Labels (248):	"Rel X" (131), "Rel Y" (132)
	Button Labels (249):	"Button Left" (124), "Button Middle" (125), "Button Right" (126), "Button Wheel Up" (127), "Button Wheel Down" (128)
	Evdev Middle Button Emulation (250):	0
	Evdev Middle Button Timeout (251):	50
	Evdev Wheel Emulation (252):	0
	Evdev Wheel Emulation Axes (253):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (254):	10
	Evdev Wheel Emulation Timeout (255):	200
	Evdev Wheel Emulation Button (256):	4
	Evdev Drag Lock Buttons (257):	0[/B]

I assume there is a file that I can edit somewhere.

---

### Post by mikejonesey on 2011-10-21
try playing with these three props;

> 
[B]Device Accel Constant Deceleration (242):	1.000000
	Device Accel Adaptive Deceleration (243):	1.000000
	Device Accel Velocity Scaling (244):	10.000000[/B]


eg
```
xinput set-prop 10 244 5
```

the will set;
device id 10 (your mouse)
propery id 244 (the velocity scaling prop)
to 5 (may speed up / slow down, may do nothing lol)

have fun :)

---

### Post by mikejonesey on 2011-10-21
found an interesting article on the properties for you here...

[http://www.x.org/wiki/Development/Documentation/PointerAcceleration](http://www.x.org/wiki/Development/Documentation/PointerAcceleration)

---

### Post by Quarkrad on 2011-10-23
Thank you for the info.  The machine I need to 'slow down' is out of action for a few days so I wanted to spend some time learning about this before I can log-on remotely and try some changes. (It is my mother-in-laws machine 80 miles away - I can log on remotely and change things.  Although I have the sae s/w set up on my pc via Virtuabox I do not have the same bluetooth/mouse hardware).  I think(?) te config settings under ubuntu 11.xx is now in something called HAL rater than xconfig but I'm probably wrong.  The output of your script - does it get this info from a specific file that you cab edit?   I will play (on her machine) with the terminal command suggestion you made - it is a case of inputing various commands like this or can you access a configuration file somewhere?  Sorry for all this - I'm new to linux and getting my head around how it works - I tend to like a file that I can edit rather than just inputting a terminal command that changes something somewhere that I do not know.

---

