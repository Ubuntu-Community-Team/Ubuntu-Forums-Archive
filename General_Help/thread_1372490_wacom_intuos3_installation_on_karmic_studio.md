---
title: "wacom intuos3 installation on karmic studio"
date: 2010-01-04
forum: General Help
---

### Post by ultratek on 2010-01-04
iam trying to install the latest drivers for my intuos3 tablet 9x12

i have read the howto through and through and even tried the getwacom.py script nothing seems to be working for me...

is there anyone out there that could walk me through it
i have downloaded and extracted the latest tar for the drivers into /home/razertek/linuxwacom-0.8.5-9/....using the getwacom.py

iam using a dell xps420 q6600 ubuntustudio 9.10 karmic
i suppose i am too much of a newb to just get it done on my own
and i appreciate and responses..iam determined to see this done so i can take advantage of the the latest drivers and features
thankyou

---

### Post by Favux on 2010-01-04
Hi ultratek,

I'm not clear on what isn't working for you.  Error when compiling?  No reaction to the stylus?

---

### Post by ultratek on 2010-01-05
i want to start fresh..clean install of the latest drivers...right now all my pad does is..the cursor moves when i hover my grip pen but when i touch the pad it stops in this sense and i have to touch the pad to move the cursor and click does not work.

---

### Post by Favux on 2010-01-05
Hi ultratek,

For the Intuos3 the default linuxwacom, 0.8.4-1, in Karmic should work fine.  I don't know what differences, if any, ubuntustudio introduces.

Since you have compiled and installed the latest driver make sure that xserver-xorg-input-all is installed in Synaptic Package Manager.

You may find the modified wacom.fdi is helpful.  Please see [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

---

### Post by ultratek on 2010-01-06
well i really have not got the driver compiled correctly...i dont believe

---

### Post by Favux on 2010-01-06
Hi ultratek,

Well, that could be.  Follow Appendix 4 in this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") to uninstall the one you've compiled.  New to Karmic is the fact that purging xserver-xorg-input-wacom also purges xserver-xorg-input-all.  So after you're done just reinstall xserver-xorg-input-all through Synaptic Package Manager.  That should bring along xserver-xorg-input-wacom so all you'd have left to do is install wacom-tools with Synaptic and reboot.  Things should be working at that point.

Then install the modified .fdi in post #176 and reboot again.  The 'xsetwacom list' and wacomcpl should be working at that point.

Or you could see if the current problem is the wacom.ko isn't auto-loading.  Try in a terminal:
```
lsmod | grep wacom
```
You should see 'wacom', the wacom module (wacom.ko), in the output.

---

### Post by ultratek on 2010-01-06
thank you for your help..i got the pen working and stylus back to normal...but the #176 post does not help with the xsetwacom and wacomcpl...i still get errors when i try to run those cmds

---

### Post by Favux on 2010-01-06
Hi ultratek,

Good, we're getting there.  Could you show me the output of?:
```
xinput --list
```
and
```
xsetwacom list
```

---

### Post by ultratek on 2010-01-06
```
xinput --list
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
"Razer Razer Lycosa"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
"stylus"	id=3	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 60960
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 45720
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
"Razer Razer Lycosa"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"pad"	id=5	[XExtensionKeyboard]
	Type is Wacom Pad
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 8
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 60960
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 45720
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is 0
		Max_value is 4096
		Resolution is 1
	Axis 4 :
		Min_value is 0
		Max_value is 4096
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"cursor"	id=6	[XExtensionKeyboard]
	Type is Wacom Cursor
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 60960
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 45720
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
	Axis 4 :
		Min_value is -1023
		Max_value is 1023
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"eraser"	id=7	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 60960
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 45720
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Razer Razer Mamba"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
"Power Button"	id=9	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=10	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=11	[XExtensionPointer]
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
"Razer Razer Mamba"	id=12	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 15
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
xsetwacom list
xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
```

---

### Post by Favux on 2010-01-06
Hi ultratek,

Ok, xinput looks good so the .fdi is in place.

Hmmm, why would a distribution package installed through Synaptic miss a depency?  Anyway search Synaptic Package Manager for 'libxcb-xlib' and then install it and reboot.  You should just want the library, not a file that ends with -dev or -dbg.  Hopefully there isn't a whole chain of dependencies missing.

---

### Post by ultratek on 2010-01-07
well i have looked for that file in synaptic but it is not in the list

---

### Post by ultratek on 2010-01-07
i just need a setting where i can confine the cursor to one monitor out of two.

---

