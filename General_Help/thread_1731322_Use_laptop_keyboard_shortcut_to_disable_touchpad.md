---
title: "Use laptop keyboard shortcut to disable touchpad?"
date: 2011-04-17
forum: General Help
---

### Post by CrazeDIzzleD on 2011-04-17
I have an Asus K6LIC laptop. In Windows if I press function+F9, it toggles my touchpad on and off. I'm wondering if I can get this functionality in Ubuntu 10.10. All other function keys work, except for this one. The only thing I can find is to permanently disable the touchpad, which is not what I want to do.

---

### Post by rummy77 on 2011-04-18
I posted on another thread that the simple solution I use is by opening a terminal (Ctrl+Alt+t) and enter ```
synclient TouchpadOff=2
```

The variable (after the "=") can be set to:
0 - touchpad is on and works like normal
1 - touchpad is completely off
2 - touchpad is on but tap-clicking is off

This might work for you.

---

### Post by Krytarik on 2011-04-18
You can create a keyboard shortcut for this command, to toggle the touchpad on and off:
```
gconftool-2 /desktop/gnome/peripherals/touchpad/touchpad_enabled --toggle
```Greetings.

---

### Post by Quiver on 2011-04-18
> You can create a keyboard shortcut for this command, to toggle the touchpad on and off:
Code:

gconftool-2 /desktop/gnome/peripherals/touchpad/touchpad_enabled --toggle

Greetings. 

Thank you!  This worked for me on my Asus EeePC.

The synclient command didn't work. Using ```
synclient -l
``` I could see that the TouchpadOff value wouldn't change from 0.

---

