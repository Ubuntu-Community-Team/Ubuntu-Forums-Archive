---
title: "power button doesn't work"
date: 2011-10-15
forum: General Help
---

### Post by elliotn on 2011-10-15
the power button in kubuntu 11.04 is not working, anyway to fix it.?

---

### Post by elliotn on 2011-10-15
bump

---

### Post by elliotn on 2011-10-17
what I have to do to get answers

---

### Post by mutley89 on 2011-10-17
You mean the physical power button on your computer, which is doing nothing when you press it and you want it to shutdown, yes?
If so run "xev" from an xterm, you'll get a small white window which will produce output when you press keys.  Try pressing the power button, you should get a few lines od output resembling the following each time you press the power button:
```
KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   16  
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 35, synthetic NO, window 0x4600001,
    root 0xac, subw 0x0, time 14802995, (183,475), root:(187,493),
    state 0x10, keycode 124 (keysym 0x1008ff2a, XF86PowerOff), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```If you don't get any output from this I have no idea how to help you. If you do try setting a custom shortcut in the settings menu to run the following when you press the power button:
```
 
qdbus org.kde.ksmserver /KSMServer org.kde.KSMServerInterface.logout 1 2 2 
```

---

