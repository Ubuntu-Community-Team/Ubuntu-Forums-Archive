---
title: "Xmodmap configuration"
date: 2012-03-25
forum: General Help
---

### Post by ctheory9 on 2012-03-25
On my Ubuntu machine Ctrl+Alt+F1 is bound to a virtual terminal. I can see the corresponding entry by running xmodmap -pke

keycode 67 = F1 XF86_Switch_VT_1 F1 XF86_Switch_VT_1
Per this thread ([http://superuser.com/questions/189869/xmodmap-six-characters-to-one-key](http://superuser.com/questions/189869/xmodmap-six-characters-to-one-key)), which I might add is consistent with what I've read elsewhere, the columns on the right hand side of '=' correspond to

key, Shift+key, AltGr+key, Shift+AltGr+key

Given that, I don't understand how the keycode mapping for F1 (above) works for Ctrl+Alt+F1. It seems it should really be either Shift+F1 or Shift+AltGr+F1?

Here's the output of xmodmap -pm on my machine:

shift Shift_L (0x32), Shift_R (0x3e)
lock Caps_Lock (0x25)
control Control_L (0x42), Control_R (0x69)
mod1 Alt_L (0x40), Alt_R (0x6c), Meta_L (0xcd)
mod2 Num_Lock (0x4d)
mod3 
mod4 Super_L (0x85), Super_R (0x86), Super_L (0xce), Hyper_L (0xcf)
mod5 ISO_Level3_Shift (0x5c), Mode_switch (0xcb)

Please explain. Thanks!

---

