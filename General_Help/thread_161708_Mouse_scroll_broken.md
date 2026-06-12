---
title: "Mouse scroll broken"
date: 2006-04-17
forum: General Help
---

### Post by tokez on 2006-04-17
heres my xorg.conf

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option      "Emulate3Buttons" "true"
	Option      "Buttons" "7"
        Option      "ZAxisMapping" "4 5"
	Option      "ChordMiddle"
	Option      "EmulateWheel" "1"
EndSection

my down scroll button works - but up scroll does not
figured downscroll to be button 5.

---

### Post by prizrak on 2006-04-17
There needs to be more info. Do you have a touchpad or regular mouse? If you are using a touchpad there is a good guide [here]("http://doc.gwos.org/index.php/Alps_touchpad") that I used on a Toshiba even tho it's for Sony.

---

### Post by tokez on 2006-04-17
its just a regular mouse with a scroll wheel that is also a button.
i think its because i overlooked a step in installation when i reinstalled breezy, but there should be a quickfix.

whats the command to re run the hardware detetion if there is one. 

thanks

---

### Post by tokez on 2006-04-17
easy quick fix =

sudo dpkg-reconfigure xserver-xorg

go thru the setup and make sure to select yes for Enable scroll events ... all i did was overlook this :P

---

### Post by prizrak on 2006-04-18
:) Glad it's working now :)

---

