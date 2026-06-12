---
title: "Need terminal command help"
date: 2010-08-18
forum: General Help
---

### Post by Vanillalite on 2010-08-18
So I'm a terminal newbie, but found a fix for a problem I'm having searching the web that involves the terminal. 

Basically my USB gravis gamepad thinks itself is a mouse. I found a bug thread and fix [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/418470"), but I don't understand the coding at the end.

```
quickfix:
use the command xinput set-props <device-id> <option-id> 0
to set mouse events and keyboard events to false for the joystick/gamepad
the respective id can be found by running
xinput list
and
xinput list-props <device-id>
```

I typed in for the list and found out my pad is id=8. I'm not sure about the initial command though. Do I put id=8 for my device-id or just 8? Also I don't get what my option-id is suppose to be? Do I need the <>'s or not? Also what's the 0 at the end for?

Thanks in advance ubuntu peeps! :D

PS: If it matters I'm running Ubuntu 10.04 amd64.

---

### Post by kbless7 on 2010-08-18
for the <device-id> just put 8. As for the <option-id> that would be the one that specifies the mouse and keyboard events to be false for the joystick/gamepad... not sure of this option. Then the 0 would specify that option to be false

---

### Post by Vanillalite on 2010-08-18
> **kbless7 said:**
> ```
xinput list-props 8
```

Doesn't that just list things and not actually change anything? I'm confused by this answer.

---

### Post by kbless7 on 2010-08-18
Try this:

run
```
xinput list
```
to find the id for your mouse and keyboard

then run
```
xinput list-props <device-id>
```
to find the option for each device that says joystick/gamepad, where <device-id> will be just the number

finally run
```
xinput set-props <device-id> <option-id> 0
```
where <option-id> is the number you got from the 2nd code section

this is what your link is saying. now if your gamepad is acting like a mouse then you'll want to use the 2nd code block to find the options for the gamepad that'll make it work like a mouse, and then disable them with the 3rd code block

---

### Post by Vanillalite on 2010-08-18
```
xinput list-props <device-id>
```

I did that, but I'm confused on my output in terms of what exactly my option id is. I get...

```
xinput list-props 8
Device 'Gravis GamePad Pro USB ':
	Device Enabled (142):	1
	Device Accel Profile (258):	0
	Device Accel Constant Deceleration (259):	1.000000
	Device Accel Adaptive Deceleration (261):	1.000000
	Device Accel Velocity Scaling (262):	10.000000
	Debug Level (264):	0
	Buttons (265):	10
	Axes (266):	2
	Generate Mouse Events (267):	1
	Generate Key Events (268):	1
	Axis Deadzone (269):	5000, 5000
	Axis Type (270):	1, 1
	Axis Mapping (271):	1, 2
	Axis Amplify (272):	1.000000, 1.000000
	Axis Keys (low) (273):	0, 0, 0, 0, 0, 0, 0, 0
	Axis keys (high) (274):	0, 0, 0, 0, 0, 0, 0, 0
	Button Mapping (275):	5, 5, 5, 0, 0, 0, 0, 0, 0, 0
	Button Number (276):	1, 2, 3, 0, 0, 0, 0, 0, 0, 0
	Button Amplify (277):	1.000000, 1.000000, 1.000000, 1.000000, 1.000000, 1.000000, 1.000000, 1.000000, 1.000000, 1.000000
	Button Keys (278):	0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0

```

---

### Post by oldfred on 2010-08-19
As I read your instructions you want to change the 1 to 0 for these two:

    Generate Mouse Events (267):    1
    Generate Key Events (268):    1

use the command xinput set-props <device-id> <option-id> 0
to set mouse events and keyboard events to false for the joystick/gamepad
the respective id can be found by running

xinput set-props 8 267 0
xinput set-props 8 268 0

Then rerun list to see that the settings have changed.

---

### Post by Vanillalite on 2010-08-19
Okay now those instructions make total sense to me OldFred.

Problem I'm running into now is it appears xinput commands have changed compared to when the posts in that bug page were made.

xinput set-props No longer seems to be a viable command. I totally get what I need to change and I see the values, but I'm not sure what command to use. When I try the old command it doesn't work, and just gives me a list of xinput commands.

```
xinput get-feedbacks <device name>
	xinput set-ptr-feedback <device name> <threshold> <num> <denom>
	xinput set-integer-feedback <device name> <feedback id> <value>
	xinput get-button-map <device name>
	xinput set-button-map <device name> <map button 1> [<map button 2> [...]]
	xinput set-pointer <device name> [<x index> <y index>]
	xinput set-mode <device name> ABSOLUTE|RELATIVE
	xinput list [--short || --long] [<device name>...]
	xinput query-state <device name>
	xinput test [-proximity] <device name>
	xinput create-master <id> [<sendCore (dflt:1)>] [<enable (dflt:1)>]
	xinput remove-master <id> [Floating|AttachToMaster (dflt:Floating)] [<returnPointer>] [<returnKeyboard>]
	xinput reattach <id> <master>
	xinput float <id>
	xinput set-cp <window> <device>
	xinput test-xi2 <device>
	xinput list-props <device> [<device> ...]
	xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...]
	xinput set-float-prop <device> <property> <val> [<val> ...]
	xinput set-atom-prop <device> <property> <val> [<val> ...]
	xinput watch-props <device>
	xinput delete-prop <device> <property>
	xinput set-prop <device> [--type=atom|float|int] [--format=8|16|32] <property> <val> [<val> ...]

```

Now that final line seems to be what I need but I'm not sure about what to fill in. I get that <device> would be 8 since that's my id. I assume the two vals at the end are the values aka the 1 or 0 that I need, but not sure which goes where. In between device and val though I don't get what it's wanting from me.

Thanks for all your help so far guys. I feel like I'm close, but not quite there.

---

### Post by Vanillalite on 2010-08-20
I've tried somethings, but nothing has worked. I just don't think I'm doing the xinput terminal commands right.

---

