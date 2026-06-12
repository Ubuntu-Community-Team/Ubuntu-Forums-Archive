---
title: "Remapping Keys"
date: 2011-03-26
forum: General Help
---

### Post by rtobyr on 2011-03-26
A quick Google search led me to several posts about remapping keys with xev & xmodmap. My apostrophe/quote key is broken, so I want to re-map those characters to the backward-apostrophe/tilde button. Therefore, I cannot press the key to find out what its code is with xev. Is there a GUI program for remapping keys in 10.10 that does not require me to press the key that I want to assign to a different key?

---

### Post by TeoBigusGeekus on 2011-03-26
Output of xev on my system when I press ':
```
KeyPress event, serial 39, synthetic NO, window 0x1400001,
    root 0x1ad, subw 0x0, time 1226505, (-65,-78), root:(486,706),
    state 0x10, keycode 48 (keysym 0x27, apostrophe), same_screen YES,
    XLookupString gives 1 bytes: (27) "'"
    XmbLookupString gives 1 bytes: (27) "'"
    XFilterEvent returns: False

KeyRelease event, serial 39, synthetic NO, window 0x1400001,
    root 0x1ad, subw 0x0, time 1226584, (-65,-78), root:(486,706),
    state 0x10, keycode 48 (keysym 0x27, apostrophe), same_screen YES,
    XLookupString gives 1 bytes: (27) "'"
    XFilterEvent returns: False
```

---

