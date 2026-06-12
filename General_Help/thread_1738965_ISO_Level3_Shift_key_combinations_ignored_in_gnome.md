---
title: "ISO_Level3_Shift key combinations ignored in gnome"
date: 2011-04-25
forum: General Help
---

### Post by alfonz19 on 2011-04-25
xev reports that correct keys are being pressed, but any other application is unable to print "&#367;" symbol.

```

KeyPress event, serial 33, synthetic NO, window 0x4200001,
    root 0x18f, subw 0x0, time 934615, (80,-12), root:(81,66),
    state 0x10, keycode 133 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x4200001,
    root 0x18f, subw 0x0, time 934724, (80,-12), root:(81,66),
    state 0x98, keycode 47 (keysym 0x1f9, uring), same_screen YES,
    XLookupString gives 2 bytes: (c5 af) "&#367;"
    XmbLookupString gives 2 bytes: (c5 af) "&#367;"
    XFilterEvent returns: False

```

---

