---
title: "Use AltGR (Right Alt) instead of Alt?"
date: 2006-05-18
forum: General Help
---

### Post by stuporglue on 2006-05-18
I'd like to use AltGR to be the mouse button modifier in Gnome. I've tried several options in gconf-editor, but nothing seems to make it work. 

gconf key is here:
/apps/metacity/general/mouse_button_modifier

Default is Alt. I've tried AltGR, Alt_R, and Alt_GR with no success.  Does anyone know how to make this work? 

My AltGR key gives funny results in xev too. Here's the output of normal (Left) Alt (one is key down, one is key up):
```

KeyPress event, serial 26, synthetic NO, window 0x3000001,
    root 0x5c, subw 0x0, time 1251692675, (422,616), root:(432,689),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3000001,
    root 0x5c, subw 0x0, time 1251693253, (422,616), root:(432,689),
    state 0x8, keycode 64 (keysym 0xffe7, Meta_L), same_screen YES,
    XLookupString gives 0 bytes:
```

My AltGR (Right) Alt gives this (one is key down, one is key up):
```
PropertyNotify event, serial 29, synthetic NO, window 0x3000001,
    atom 0x110 (XKLAVIER_STATE), time 1251742989, state PropertyNewValue

PropertyNotify event, serial 29, synthetic NO, window 0x3000001,
    atom 0x110 (XKLAVIER_STATE), time 1251742990, state PropertyNewValue
```

Any help is greatly appreciated!

Thanks,

Michael Moore

---

### Post by AikonIV on 2008-07-15
gconf-editor seems to refer to AltGR as <Mod5>.

(Sorry about raising this ancient thread, but it came up as the third result when I first googled for this, and there's nothing in the first page with the answer, so hopefully this will help somebody.)

---

