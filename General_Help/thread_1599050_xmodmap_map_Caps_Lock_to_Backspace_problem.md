---
title: "xmodmap: map Caps_Lock to Backspace problem"
date: 2010-10-17
forum: General Help
---

### Post by lejboua on 2010-10-17
Hi,

I'm using Ubuntu 10.10 and I wanted to map Caps_Lock to BackSpace and Shift + Caps_Lock to the Caps_Lock normal behaviour, so I wrote the following on my ~/.Xmodmaprc (my Caps_Lock key has the code 66):
```

clear lock
keycode 66 = BackSpace Caps_Lock
add lock = Caps_Lock

```

After running "xmodmap ~/.Xmodmaprc" the Shift + Caps_Lock acts as expected; Caps_Lock acts as the BackSpace but *also* activates the Caps_Lock key. Pressing Caps_Lock without any modifiers triggers BackSpace (using xev):
```

KeyPress event, serial 36, synthetic NO, window 0x4800001,
    root 0x15a, subw 0x0, time 341730, (15,-17), root:(740,38),
    state 0x10, keycode 66 (keysym 0xff08, BackSpace), same_screen YES,
    XKeysymToKeycode returns keycode: 22
    XLookupString gives 1 bytes: (08) "
    XmbLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4800001,
    root 0x15a, subw 0x0, time 342282, (15,-17), root:(740,38),
    state 0x12, keycode 66 (keysym 0xff08, BackSpace), same_screen YES,
    XKeysymToKeycode returns keycode: 22
    XLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

```

Maybe it's some other option in Gnome that's conflicting with my Caps_Lock = BackSpace. Can somebody give me a tip here?

Also, I've read that I have to run "xset r 66" to enable repetition on my Caps_Lock. On which file can I place "xset r 66" to enable this when Ubuntu starts?

Thanks in advance!

---

