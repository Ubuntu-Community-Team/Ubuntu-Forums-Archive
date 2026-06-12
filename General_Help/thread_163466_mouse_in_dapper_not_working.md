---
title: "mouse in dapper not working"
date: 2006-04-20
forum: General Help
---

### Post by tokez on 2006-04-20
i just installed dapper drake and finally got visuals when i switched to the vesa driver. however, now my mouse does not work. im moving around with just keyboard shortcuts and terminal commands atm so i will try to get as much info to help as possible.

heres my mouse portion in xorg.conf -- i hope this is all you need from xorg

[code]

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

let me know if you need anymore info and ill try to retrieve it for you. thanks --

ps: i tried dpkg-reconfigure xserver-xorg and switched answers in the mouse configuration but that did not correct it.

---

### Post by tokez on 2006-04-21
i believe the problem was with my hardware. new mouse = fix.

---

