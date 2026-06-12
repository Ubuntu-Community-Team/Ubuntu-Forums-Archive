---
title: "No three finger + multitouch"
date: 2011-08-03
forum: General Help
---

### Post by marpi.evolve on 2011-08-03
Hey,

My mouse pad will not function for gestures requiring more than two fingers.  It's a synaptics touch pad, but I don't know how to find the exact model.. the computer is a Gateway NV53A61U.

geistest returns

Device 12 added
	attr "device name" = "SynPS/2 Synaptics TouchPad"
	attr "device id" = 12
	attr "direct touch" = false
	attr "independent touch" = false
	attr "device touches" = 4
	attr "Abs MT Position X 0 min" = 1472.000000
	attr "Abs MT Position X 0 max" = 5772.000000
	attr "Abs MT Position X 0 resolution" = 0
	attr "Abs MT Position Y 1 min" = 1408.000000
	attr "Abs MT Position Y 1 max" = 5086.000000
	attr "Abs MT Position Y 1 resolution" = 0
	attr "Abs MT Tracking ID 2 min" = 0.000000
	attr "Abs MT Tracking ID 2 max" = 65535.000000
	attr "Abs MT Tracking ID 2 resolution" = 0

but upon multi finger presses it just pretends it's two fingers. 


and if run lsinput, I find out my touch pad is on event 9

/dev/input/event9
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 433
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

and if I run mtdev-test on it it says it can't grab the device.

# sudo mtdev-test /dev/input/event9
error: could not grab the device

Any advice? I've been searching the internet for a while, can't seem to find a solution.

And the weirdest thing is that if I'm in the terminal and I three finger tap, it pastes random text..  not even text in my clipboard, but stuff randomly in web pages I've been on / have open.

---

