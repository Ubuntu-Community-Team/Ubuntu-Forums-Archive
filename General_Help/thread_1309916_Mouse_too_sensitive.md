---
title: "Mouse too sensitive"
date: 2009-11-01
forum: General Help
---

### Post by triplesick on 2009-11-01
Hi--

i just got this razer 3500dpi mouse, which i love, except that it's so sensitive that it's nearly unusable in ubuntu.  i have the sensitivity and acceleration sliders dragged all the way down.  is there a way to reduce sensitivity further?

thanks.

---

### Post by triplesick on 2009-11-08
lol?

---

### Post by triplesick on 2009-11-14
bippity bop?  i imagine i would have to recompile something, eh?  looking to terminal commands, it would seem that the lowest meaningful value i can enter = slider at its lowest setting.  setting 0.00000001 value does nothing.  eh?

---

### Post by 3Dragz on 2009-11-15
I think Phoronix has something on this with the deathadder. This link might get you where you need to go. Dunno if it will help or not.

[http://www.phoronix.com/scan.php?page=news_item&px=NTk4NQ](http://www.phoronix.com/scan.php?page=news_item&px=NTk4NQ)

---

### Post by Raiju on 2009-11-15
^^Or
if you have a computer/partition running windows install the driver, set the DPI then boot into linux, the setting should be saved to the mouse to use on other computers.
My Death Adder did anyway.

---

### Post by triplesick on 2009-11-17
@3Dragz: Thanks!  I looked into that fellow's tool, but I have to compile it myself and it have run into a weird error trying to do so.  At least it's a start.  If I figure it out, I'll post the result.

@Raiju: what an excellent solution that would be, but for some reason it ain't happenin' for me.  thanks though.

---

### Post by Tamale on 2010-09-29
> **triplesick said:**
> Hi--

i just got this razer 3500dpi mouse, which i love, except that it's so sensitive that it's nearly unusable in ubuntu.  i have the sensitivity and acceleration sliders dragged all the way down.  is there a way to reduce sensitivity further?

thanks.

much easier to use this:

[http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/)

Open a terminal
Run the command: xinput --list --short
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Razer USA, Ltd DeathAdder Mouse         	id=6	[slave  pointer  (2)]
&#9116;   &#8627; Razer USA, Ltd DeathAdder Mouse         	id=7	[slave  pointer  (2)]
&#9116;   &#8627; Razer DeathAdder                        	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                  	id=10	[slave  keyboard (3)]
Note the name of your device. In my case, manipulating ‘Razer DeathAdder’ worked.
Set the constant deceleration for the device:
xinput --set-prop "Razer DeathAdder" "Device Accel Constant Deceleration" 5
That’s it. You might have to play around with the value, but 5 slowed down my mouse sufficiently.

To see the current settings for the device:
xinput --list-props "Razer DeathAdder"
To turn off mouse acceleration:
xinput --set-prop "Razer DeathAdder" "Device Accel Velocity Scaling" 1
To perform the tuning automatically, I simply created a file containing the script below, ran chmod +x on it and added it to System -> Preferences -> Startup Applications in GNOME:

#!/bin/sh
xinput --set-prop "Razer DeathAdder" "Device Accel Constant Deceleration" 5
xinput --set-prop "Razer DeathAdder" "Device Accel Velocity Scaling" 1

---

### Post by dargaud on 2010-11-11
Excellent tip. I just don't know why this sensitivity setting doesn't get added to the KDE mouse panel...
I just want to add that if you get the message:
```
$ xinput --set-prop "Logitech G9 Laser Mouse" "Device Accel Constant Deceleration" 5
Warning: There are multiple devices matching 'Logitech G9 Laser Mouse'.
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.
unable to find device Logitech G9 Laser Mouse

```
(I have no idea why the device is duplicated, it's not even present in my xorg.conf). Then you can use:
```
$ xinput --list --short
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech G9 Laser Mouse                   id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech G9 Laser Mouse                   id=9    [slave  pointer  (2)]

$ xinput --set-prop 8 "Device Accel Constant Deceleration" 5

```

---

