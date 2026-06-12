---
title: "Please help me set the mouse vertical scroll"
date: 2009-11-08
forum: General Help
---

### Post by jessebean on 2009-11-08
I'm trying to follow related discussions on how to set the vertical scroll default, but they are using dated xorg.conf settings, where now it's hal-based.

I'm confused by these settings.  Supposedly there should be a "Configured Mouse" along with the Mac and Dell devices.  I want to set the scroll to 3, from 1 (I use the scroll on the volume manager very frequently, and it works best at 3).  Thanks in advance for your help.

```
$ xinput list
```
[INDENT][SIZE="2"]> "Virtual core pointer"	id=0	[XPointer]
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
  .
  .
  .
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
		Resolution is 1[/SIZE][/INDENT]

---

