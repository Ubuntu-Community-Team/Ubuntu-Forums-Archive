---
title: "Alt-Gr key not working in some programs"
date: 2012-07-26
forum: General Help
---

### Post by kovesz on 2012-07-26
Hi,

I use Ubuntu 11.04 (Natty) with a Hungarian keyboard. I use the Ubuntu Classic display. Recently I have installed French locales and since then I cannot use my Alt-Gr in some programs to type brackets and symbols like {,&,#. 

I am not sure exactly when this problem started, maybe it wasn't caused by installing French on my Ubuntu. It could also have been a regression caused by an update.

Examples of programs that have this problem: gedit, chrome, the "Keyboard preferences" dialogue

Examples of programs that work correctly: gVim, emacs, gnome-terminal

xmodmap output is:
```
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

Using xev I have verified that the Alt-Gr key (keycode 108 ) is attached to ISO_Level3_Shift.

I have read some forum topics with similar problems but could not solve the problem. Please give advice about what could I do.

Thanks,

kovesz

---

