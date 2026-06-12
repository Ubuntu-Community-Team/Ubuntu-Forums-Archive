---
title: "imps/2 vs. explorerps/2 w/ kvm and side buttons"
date: 2006-03-26
forum: General Help
---

### Post by usr on 2006-03-26
i have an intellimouse optical usb (w/ ps/2 adapter) plugged into a belkin 4-port kvm.  i originally configured my xorg.conf with the explorerps/2 protocol in order to get my side buttons working (which they did).

however, switching inputs on the kvm and coming back to my kubuntu box causes the mouse to lose sync ([http://bugzilla.kernel.org/show_bug.cgi?id=2082](http://bugzilla.kernel.org/show_bug.cgi?id=2082)).  i can fix this by unplugging/replugging the mouse back into the kvm, rebooting, sudo modprobe -r/a psmouse, etc.  in looking for a more perminent solution, i came across the suggestion to use imps/2 instead of explorerps/2 in my xorg.conf.  

this fixes the kvm sync problem, but breaks the side buttons on the mouse.  xev does not see anything at all when pressing the side buttons while using imps/2.

here is my current xorg.conf:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"7"
EndSection 

obviously the ultimate goal would be to have the side buttons working and no problems with the kvm.  so, i either need a way to fix the side buttons while using imps/2, or a better solution to the kvm problem while using explorerps/2.

thanks in advance.

---

### Post by usr on 2006-04-01
any suggestions/links/tips?  anything?

---

