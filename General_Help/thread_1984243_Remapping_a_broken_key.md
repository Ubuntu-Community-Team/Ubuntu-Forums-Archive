---
title: "Remapping a broken key"
date: 2012-05-21
forum: General Help
---

### Post by cezar_dan on 2012-05-21
After giving my laptop to someone to repair my monitor, when I got ot back I noticed my left shift key was broken. I've been using it since I started using keyboards and it's hard to readjust to using the right shift.

I've tried to remap the windows key to take on the role of right shift with xev and xmodmap commands (I can't find out the keycode for left shft) and it didn't work.

Is there another way to do this?

---

### Post by kanikilu on 2012-05-21
I'd imagine xmodmap would be the way to go, but it's been a long time since I needed to use it. If all you need is the information for Shift_L, here's what I get in xev:

```
KeyPress event, serial 36, synthetic NO, window 0x5400001,
    root 0xb5, subw 0x0, time 8768600, (10,-17), root:(64,35),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

