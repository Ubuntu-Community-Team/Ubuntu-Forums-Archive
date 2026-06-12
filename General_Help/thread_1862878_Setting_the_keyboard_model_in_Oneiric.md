---
title: "Setting the keyboard model in Oneiric?"
date: 2011-10-17
forum: General Help
---

### Post by DreymaR on 2011-10-17
Having happily upgraded to Ubuntu 11.10, I noticed that the keyboard model choice is now missing from they Keyboard Preferences app. That won't do; I very much need to set the model to the one I'm using which isn't pc105 as it says now!

I tried looking at etc/X11/xorg.conf which sent me to /etc/default/keyboard (as expected) but that file doesn't seem to be read anymore; at least, not using Unity? At any rate, the settings there aren't the ones active on my system now and they also don't seem to be what I get if I press the "Reset to defaults" button in Keyboard Preferences.

[Update: A full system restart seems to have activated the /etc/default/keyboard file, as I now get the default layout settings from that. But:
- The options don't seem to work? If I select Reset to defaults all options become deselected rather than the ones in the keyboard file
- The model, interestingly, now shows up correctly using "Show Current Layout" BUT the actual key presses are still pc105 ones. My keycodes component isn't active although it would appear that the geometry component has kicked in.
A machine restart after clearing /var/lib/xkb didn't help.]

HALP?

---

### Post by DreymaR on 2011-10-24
New update:

Okay, so the right way to switch keyboard model seems to be a manual edit of /etc/default/keyboard then?!

Turns out the reason for my failure in the previous attempt was a malformed evdev file in my xkb/rules folder. Sorry about that. All is well as ends well.

---

