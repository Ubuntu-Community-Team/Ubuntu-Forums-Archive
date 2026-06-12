---
title: "Under the 11.10 Bonnet - mouse speed"
date: 2011-11-16
forum: General Help
---

### Post by Quarkrad on 2011-11-16
Running 11.10  My mouse speed is set to the lowest speed setting via the gui in System Settings/Mouse and Touchpad - but it is far too fast.  I need to go 'under the bonnet', if possible, to slow it down.  The mouse is bluetooth attached and I have had some help in identifying it, it is recognized as a Logitech device with an id of 10.   I have tried this suggested command **xinput set-prop 10 244 5** but it makes no difference.  Google searches talk about /etc/X11/xorg.config - mine looks like this:-


[B]Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection[/B]


but other google threads speak about HAL for the latest versions.  As a newbie I'm now trying to  find about HAL but I'm struggling a bit 'under the bonnet'. Is it possible to change/add something to slow the mouse speed down?  Any advice much appreciated.

---

### Post by hwttdz on 2011-11-16
Get the id of your mouse device:
```
xinput --list --short
```
should be a number (mine is 8 )

list the possible properties of what you want to change
```
xinput --list-props 8
```
but you should use your number.

Fiddle with settings, I saw I had a "Device Accel Velocity Scaling", so I tried:
```
xinput set-prop 8 "Device Accel Velocity Scaling" 50
```
where 8 is the id of the device I was playing with and 50 was the value I put it to.  1 is very slow, like way mega slow, and 50 is pretty ridiculously fast.  

There seem to be a lot of options on mine... "Device Accel Constant Deceleration", "Device Accel Adaptive Deceleration", "Device Accel Velocity Scaling" all seem to apply to "spped", and I guess if you wanted to go really crazy, you could change the value of "Coordinate Transformation Matrix".

Also, you can look at:
```
usage: xinput set-ptr-feedback <device name> <threshold> <num> <denom>
```

---

