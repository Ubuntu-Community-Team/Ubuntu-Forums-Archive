---
title: "klipper hotkeys lost on reboot."
date: 2011-05-14
forum: General Help
---

### Post by enimeizoo on 2011-05-14
Hello,
I have a problem with klipper hotkeys. On reboot, they are saved in ~/.kde/share/config/kglobalshortcutrc but don't work anymore. they are visible in "system settings > keyboard and mouse > global shortcuts" in the klipper tab, but just wont work. However, they are not set if I try to access them by klipper menu "right click > configure klipper > shortcuts"

It seems that shortcuts aren't even noticed by kde : 
xev's output from a successful shortcut  ( alt+g) (notice the focusout/focusin instead of the keypress):
```

KeyPress event, serial 33, synthetic NO, window 0x4e00001,
    root 0x9c, subw 0x0, time 1114251, (-62,702), root:(902,725),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 33, synthetic NO, window 0x4e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x4e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   4   0   0   1   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 33, synthetic NO, window 0x4e00001,
    root 0x9c, subw 0x0, time 1114813, (-62,702), root:(902,725),
    state 0x18, keycode 42 (keysym 0x67, g), same_screen YES,
    XLookupString gives 1 bytes: (67) "g"
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4e00001,
    root 0x9c, subw 0x0, time 1115030, (-62,702), root:(902,725),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
When trying a klipper shortcut, I get all of the events, just like the shortcut didnt exist.  (ctrl+up)
```

KeyPress event, serial 33, synthetic NO, window 0x5000001,
    root 0x9c, subw 0x0, time 2017189, (730,738), root:(734,761),
    state 0x10, keycode 105 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x5000001,
    root 0x9c, subw 0x0, time 2017688, (730,738), root:(734,761),
    state 0x14, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5000001,
    root 0x9c, subw 0x0, time 2017728, (730,738), root:(734,761),
    state 0x14, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5000001,
    root 0x9c, subw 0x0, time 2018130, (730,738), root:(734,761),
    state 0x14, keycode 105 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


```
But it's here, in ~/.kde/share/config/kglobalshortcutrc :
```
[klipper]
_k_friendly_name=Klipper
clipboard_action=Ctrl+Alt+X,Ctrl+Alt+X,Enable Clipboard Actions
cycleNextAction=Ctrl+Down,Ctrl+Alt+Down,Next history item
cyclePrevAction=Ctrl+Up,Ctrl+Alt+Up,Previous history item
edit_clipboard=Ctrl+²,Ctrl+Alt+E,&Edit Contents...
repeat_action=Ctrl+Alt+R,Ctrl+Alt+R,Manually Invoke Action on Current Clipboard
show_klipper_popup=Ctrl+Alt+V,Ctrl+Alt+V,Show Klipper Popup-Menu

```I can find none of these in the klipper config menu, but I have them in the kde global shortcuts under klipper tab. So my questions are :  why this difference? What is the file klipper takes his shortcuts from?

---

### Post by enimeizoo on 2011-05-14
It seems that klipper starts too early (before processes that should give it the infos or something). I just solved it by asking kde not to start klipper, but by putting it in my .profile (last line).

---

### Post by piccobello on 2011-12-07
> **enimeizoo said:**
> It seems that klipper starts too early (before processes that should give it the infos or something). I just solved it by asking kde not to start klipper, but by putting it in my .profile (last line).

I have the same problem and starting klipper later does not solve it for me. In my case the issue may be do to upgrading, as global shortcuts work as expected on a fresh account.

---

