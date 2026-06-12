---
title: "How to turn off touchpad on DM9"
date: 2010-05-11
forum: General Help
---

### Post by JEBB on 2010-05-11
With 9.04UNR it was possible to turn off the touchpad in the mouse control but it doesn't appear to be there in in 10.04.  Is that still possible with 10.04?  If so, where do I look for it?  Thanks.

Why you ask.  Well on the Dell Mini 9 the touchpad is always in the way when typing and very sensitive.

---

### Post by Zorael on 2010-05-11
While we wait for someone with GNOME knowledge to drop in with a good answer, there is a terminal solution. You can create a script to run a command whenever you want to disable it, and then have said script autostart upon login if you so wish.

This is *assuming* your pad is a Synaptics pad.
[indent]Pop up a text editor and paste the following.
```
#!/bin/bash

DEVICE=**[COLOR="RoyalBlue"]"SynPS/2 Synaptics TouchPad"[/COLOR]**
PROPERTY="Device Enabled"
VALUE=**[COLOR="Red"]0[/COLOR]**

echo "Setting $DEVICE: $PROPERTY ($VALUE)"

xinput set-int-prop $DEVICE $PROPERTY 8 $VALUE
```
Changing the **VALUE=[color="red"]0[/color]** line to **VALUE=[color="red"]1[/color]** makes the script enable it again.

Save it someplace (as **~/bin/touchpad-off** perhaps? but anywhere really). Also, don't forget to set it as executable ('**chmod +x ~/bin/touchpad-off**', or in Properties after right-clicking it in any file manager). [/indent]

If you *don't* have a Synaptics pad (ALPS, ElanTech, etc), it's still possible to disable it but you'd need to find out the device's name. You can find it in the output of '**xinput list**'. Example from my machine;
```
$ xinput list
&#9484; Virtual core pointer                          id=2    [master pointer  (3)]
&#9474;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9474;   &#8627; Logitech USB Receiver                     id=10   [slave  pointer  (2)]
&#9474;   &#8627; Logitech USB Receiver                     id=11   [slave  pointer  (2)]
&#9474;   &#8627; **[COLOR="RoyalBlue"]SynPS/2 Synaptics TouchPad[/COLOR]**                id=13   [slave  pointer  (2)]
&#9492; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]
```
You'll basically want to find your device in the list, and replace "**[COLOR="RoyalBlue"]SynPS/2 Synaptics TouchPad[/COLOR]**" in the script with whatever device name it has.

---

### Post by JEBB on 2010-05-12
I found the accessory Touchfreeze which is available via Synaptic. It does turn off the very sensitive touchpad on my Dell Mini 9.  But after any typing the touchpad turns back on automatically.  

The mouse control in 9.04 worked perfectly.  Is there a way of getting it back?

---

