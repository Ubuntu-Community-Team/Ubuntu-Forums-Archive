---
title: "shift not working at all"
date: 2011-03-19
forum: General Help
---

### Post by Shadowgamon on 2011-03-19
dell 1545 laptop. when shift is held the system doesn't register the input, ie no caps or symbols, but it does work for compiz shortcuts. capslock works for letters but not symbols. help

---

### Post by idoitprone on 2011-03-19
Are you sure the shift key dont register input? Install xev and run it in the terminal. It can tell you which key you are pressing. If it wrong then I am not sure how to mess with the default, so ask someone else. I only know little bit using xmodmap

---

### Post by Shadowgamon on 2011-03-19
with xev  get this from tapping shift ```
FocusOut event, serial 36, synthetic NO, window 0x7a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 36, synthetic NO, window 0x7a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  
```
when its held i get this ```
FocusOut event, serial 36, synthetic NO, window 0x7a00001,
    mode NotifyGrab, detail NotifyAncestor
``` , tested ctrl, super, along with shift in combo with other keys. all but shift gave response; shift just gave previous message

---

### Post by Shadowgamon on 2011-03-19
ive noticed now that it deselects the text field when held, if that helps

---

### Post by idoitprone on 2011-03-20
Strange there is no key code. It appears you have been copying paste random mouse movement. Are you sure you keep both open and watch the terminal as you press shift since every key has it own mapping


```
KeyRelease event, serial 40, synthetic NO, window 0x3200001,
    root 0xaa, subw 0x0, time 1882284, (273,318), root:(493,518),
    state 0x1, **keycode 50** (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

I am looking for the keycode, so i can at least write a script to map the shift key as shift. It little hacky, at least. I heard you can modift the xorg.conf file to make it default. If it really does not register then it out of my ability not sure what is going on. 



> xmodmap -pk | grep -i shift

This will tell your xmodmap contains shift.

---

### Post by Shadowgamon on 2011-03-20
mysteriously it just started working... weird. I dunno what was wrong but it seems fixed now...  oh well. I'll leave the thread open in case it stops. That's for bearing with me

---

### Post by idoitprone on 2011-03-21
> **Shadowgamon said:**
> mysteriously it just started working... weird. I dunno what was wrong but it seems fixed now...  oh well. I'll leave the thread open in case it stops. That's for bearing with me


if only our world works the same way lol

---

