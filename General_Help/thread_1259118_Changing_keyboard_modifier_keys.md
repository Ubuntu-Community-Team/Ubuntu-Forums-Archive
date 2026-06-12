---
title: "Changing keyboard modifier keys"
date: 2009-09-05
forum: General Help
---

### Post by zoqaeski on 2009-09-05
I've been playing around with my keyboard settings as part of configuring Openbox, GNOME, Vim, Emacs, etc, and I was wondering if it was possible to switch the ESC, CapsLock and left Ctrl keys such that CapsLock is mapped to ESC, Ctrl to CapsLock, and ESC to the left Ctrl key.

On a similar note, I've recently installed a similar setup on an old laptop (we're talking IBM Thinkpad, Pentium III, 1066 MHz, 256 MB RAM here) which doesn't have a Super/Windows key, and I'm trying to give it the same keybindings as my desktop Openbox configuration, so I want to get rid of CapsLock, make the CapsLock key a Ctrl key and the left Ctrl a Super key.

Can this be done?

---

### Post by darsu on 2009-09-06
The first thing I'd try is putting these lines in ~/.Xmodmap:

keycode 9 = Control_L
keycode 37 = Caps_Lock
keycode 66 = Escape

9, 37 and 66 being the keycodes of Escape, Control_L and Caps_Lock respectively.

---

