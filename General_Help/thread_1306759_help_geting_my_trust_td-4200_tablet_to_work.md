---
title: "help geting my trust td-4200 tablet to work"
date: 2009-10-30
forum: General Help
---

### Post by argor on 2009-10-30
i am using  trust td-4200 tablet
linux sees the tablet and i can move the mouse  but nothing else 


i tried to follow this guide [https://help.ubuntu.com/community/TabletSetup](https://help.ubuntu.com/community/TabletSetup)
 but the output don't match any thing :(

the output was 
USB Tablet Series Version 1.05
EHCI Host Controller
EHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller

---

### Post by Favux on 2009-10-30
Hi argor,

Use in a terminal:
```
lsusb
```
and
```
xinput --list
```
and see if you can find a name for the tablet.  Or convert 'lshal' to a txt file:
```
lshal>lshal.txt
```

---

### Post by argor on 2009-10-30
> **Favux said:**
> Hi argor,

Use in a terminal:
```
lsusb
```

 Bus 003 Device 004: ID 08ca:0010 Aiptek International, Inc. Tablet
> 
and
```
xinput --list
```
and see if you can find a name for the tablet.  Or convert 'lshal' to a txt file:
```
lshal>lshal.txt
```
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
"PS/2 Generic Mouse"	id=2	[XExtensionPointer]
	Num_buttons is 32
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
"Macintosh mouse button emulation"	id=3	[XExtensionPointer]
	Num_buttons is 32
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
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Aiptek"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
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



so it is a Aiptek Tablet do this still applies [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) ""However, the above is likely to crash xorg upon login if the tablet is plugged in"". 
has any thing chanced in the guide as nou hal is geting deprecated in 9.10(still on 9.4)
  
also thanks for the help hope i can get this to work

---

### Post by Favux on 2009-10-30
Hi argor,

You're welcome.  So it's an Aiptek tablet.  You should be able to install the Aiptek driver through Synaptic Package Manager.  If it still doesn't work it may be it needs a .fdi.  The driver package in Synaptic should automatically install a aiptek.fdi.  But in case it doesn't.

We played around with an Aiptek .fdi and came up with the one in post #50 here:  [http://ubuntuforums.org/showthread.php?t=1191826&page=5](http://ubuntuforums.org/showthread.php?t=1191826&page=5)

---

### Post by argor on 2009-10-30
> **Favux said:**
> Hi argor,

You're welcome.  So it's an Aiptek tablet.  You should be able to install the Aiptek driver through Synaptic Package Manager.  If it still doesn't work it may be it needs a .fdi.  The driver package in Synaptic should automatically install a aiptek.fdi.  But in case it doesn't.

We played around with an Aiptek .fdi and came up with the one in post #50 here:  [http://ubuntuforums.org/showthread.php?t=1191826&page=5](http://ubuntuforums.org/showthread.php?t=1191826&page=5)
it works perfect 1000 thanks :D

---

### Post by Favux on 2009-10-30
Hi argor,

Good!

---

