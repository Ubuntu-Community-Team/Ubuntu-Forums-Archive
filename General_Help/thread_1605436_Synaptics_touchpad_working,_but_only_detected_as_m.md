---
title: "Synaptics touchpad working, but only detected as mouse"
date: 2010-10-25
forum: General Help
---

### Post by k999 on 2010-10-25
I have a Fujitsu Lifebook P8110 laptop, and I've just installed Ubuntu 10.04.1. The laptop has a touchpad, which works as it should, I guess. But the tap to click is driving me insane. As I type, it gets taps, which moves the cursor and/or selects text (in other locations, other windows), so I keep writing in the wrong places, deleting text, starting multiple programs, bleh. Useless. I don't understand how anyone can live with tap to click.

OK, so I hate tap to click... Anyway, on other laptops I've had, this can be disabled in System -> Preferences -> Mouse. But I don't have the Touchpad tab in the Mouse preferences on this laptop. I've googled around, and found out that enabling SHMConfig in my xorg.conf should do the trick. I've tried various combinations, but it either stopped X from working, or didn't change a thing. When I run gsynaptics from the command line, I've not been able to fix this.

When I run "xinput list", a touchpad isn't detected at all, so it seems that my system hasn't detected the touchpad at all:


```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                         	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                         	id=9	[slave  keyboard (3)]
    &#8627; Power Button                            	id=10	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=11	[slave  keyboard (3)]
    &#8627; CNF8248                                 	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

```

If anyone has any ideas for how to disable tap to click on this system, I'd be grateful!

---

### Post by ivarn on 2010-10-25
OK try this:
Turn it off by using this command:
sudo modprobe -r psmouse 

To turn it back on:
sudo modprobe psmouse
Now, go to system>pref>keyboard shortcuts and make shortcuts for both on and off.

If you want to turn it off permanently, run the -r psmouse command and install the app gpointing-device-settings (available through the main repos).

---

### Post by k999 on 2010-10-26
Thanks for the suggestion! But when I remove the psmouse module, my mouse just stops working. :) I tried to load a couple of other modules manually to see if that helped, the ones I tried (in despair, I'll admit) were synaptics_i2c and appletouch, but none of them seemed to help.

By the way, is this what you meant? Actually making a keyboard shortcut to disable my mouse while typing, and then enabling it again when I need it? It is actually very nice not to be disturbed by that damn touchpad as I type this, but as a solution it's not really what I Was looking for. :)

---

### Post by k999 on 2010-11-07
Actually, back on my old laptop, whichi is a Toshiba Portege R500, the same is suddenly the case! It's an Ubuntu 10.04 system. Tap-to-click is enabled, System -> Preferences -> Mouse is missing the Touchpad tab, and "xinput list" doesn't show a touchpad.

What has changed? How can I fix this? The hardware has always been supported before on my Toshiba. Has nobody else experienced this?

---

