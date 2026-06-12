---
title: "How to disable key on keyboard"
date: 2010-09-18
forum: General Help
---

### Post by JohnElway on 2010-09-18
On my keyboard there's an eject key right above the delete key that I keep accidentally pressing and ejecting my flash drive. I've looked at other threads about using xev to get keycodes and xmodmap to disable them, but I don't see any keycodes anytime I press a key in the top row of the keyboard (esc, eject, F1-F19).  When I press eject this is what I get:

```
FocusOut event, serial 33, synthetic NO, window 0x4600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x4600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967245 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

Anyone see a keycode in there?

---

