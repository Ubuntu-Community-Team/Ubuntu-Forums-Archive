---
title: "default mouse settings"
date: 2006-06-08
forum: General Help
---

### Post by starkes on 2006-06-08
can anyone tell me a way to get the default mouse settings of ubuntu back? I screwed with them, and for whatever reason cant seem to get it the same again.

Maybe even just a screenshot so i can try to match them up....

---

### Post by detgar on 2006-06-08
This is how my mouse section looks.

[HTML]Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
[/HTML]

---

### Post by starkes on 2006-06-08
mine is exactly the same, but i still have different settings.

it doesnt look like the xorg.conf has much to do with sensitivity settings and whatnot...

---

### Post by andy- on 2006-07-15
I'm having same problem, xorg.conf looks same, but acceleration / sensitivity is all out of whack. Anyone know another file to edit?

---

### Post by tajreed on 2006-07-15
did u try system/preferences/mouse?

---

### Post by cyclingman on 2008-02-23
Just googled, I have the same problem, anyone out there - a screenshot would be nice! (of the system>preferences>mouse>motion tab).

---

