---
title: "Keyboard layout missing keys - Karmic Koala"
date: 2010-03-06
forum: General Help
---

### Post by tosszyx on 2010-03-06
I use in my keyboard the layout 'latam' where the '@' character is in the 'Q' Key as a third character and the shorcut for the home folder, is placed as a third character together with the '*' and the '+', so far in order to access this keys I had to press the combination 'AltGr' + 'Q' for the '@' and so on. Last week I did an upgrade to Karmic Koala, and now this keys are not working (pipe, home, at, etc.) but when I run the **xev** command, I can see the followin output:

```
KeyPress event, serial 31, synthetic NO, window 0x3400001,
    root 0x6b, subw 0x0, time 20892771, (608,746), root:(612,771),
    state 0x0, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x6b, subw 0x0, time 20892994, (608,746), root:(612,771),
    state 0x88, keycode 24 (keysym 0x40, at), same_screen YES,
    XLookupString gives 1 bytes: (40) "@"
    XmbLookupString gives 1 bytes: (40) "@"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x6b, subw 0x0, time 20893098, (608,746), root:(612,771),
    state 0x88, keycode 24 (keysym 0x40, at), same_screen YES,
    XLookupString gives 1 bytes: (40) "@"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x6b, subw 0x0, time 20893110, (608,746), root:(612,771),
    state 0x88, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```

so the symbol is there, but I don't understand why it isn't displayed in KDE, I have to copy past it everytime I want to use it.

Any suggestions ?

---

