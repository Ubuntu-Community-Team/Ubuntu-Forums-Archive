---
title: "How to configure mouse scroll?"
date: 2009-11-15
forum: General Help
---

### Post by jessebean on 2009-11-15
Here are my settings.  Please help me set the default from 0 lines of scroll to 3, by default.  The case is that the volume manager scrolls by 1% now, instead of 3%. 

```
$ xinput list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"DELL DELL USB Keyboard"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=5	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Dell Premium USB Optical Mouse"	id=6	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 18
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
```

```
$ cat /etc/X11/xorg.conf
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by Tekno.Statik on 2011-05-05
Please read & promote my idea for Ubuntu developers:

The title for the thumbnail below sucks, but I can't change it now.
Basically; Scrolling is far too limited in Ubuntu, and only Firefox offers some way out of this, but some of us prefer Chrome all day.
In my personal opinion; Chrome is just faster, and I believe Ubuntu should have custom settings for something we all do every day which is Window scrolling.

[[IMG]http://brainstorm.ubuntu.com/idea/27631/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/27631/)

---

