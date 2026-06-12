---
title: "mouse scroll wheel"
date: 2006-02-17
forum: General Help
---

### Post by Sherlock Holmboy on 2006-02-17
i have a regular 5 button mouse was messing with the xorg.config file while playing with imwheel, but now my scroll wheel doesn't work. i went back and changed xorg.config to it's original condition by running sudo dpkg-reconfigure xserver-xorg but my buttons 4 and 5 don't work right. they controlled firefox's foward and backward page navigation, but wouldn't scroll, even in other applications. 
this is my xorg.config setting for my mouse:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"		"4 5"
EndSection

```
what do i need to do? :-k

---

### Post by alfonz on 2006-02-17
try changing the emulate3button mouse to "true" instead of false

just edit the xorg file

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Sherlock Holmboy on 2006-02-17
no good, do i need to restart or anything like that for settings to take effect?

---

### Post by RAOF on 2006-02-17
You might want to add "Buttons" "7" if it's a 5 button mouse with scrollwheel   - the scroll wheel is treated as another two buttons.  That would make your mouse section:

```

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

```

---

### Post by alfonz on 2006-02-17
you need to restart your X sever

ctr+alt+backspace will restart it

---

### Post by RAOF on 2006-02-17
You'll need to restart X to get it to re-load your xorg.conf.  Log off, then press Ctrl-Alt-Backspace.  That'll kill X and get it to start again.

---

### Post by Sherlock Holmboy on 2006-02-17
the restarting of X was what i was missing. thanks a ton \\:D/

---

