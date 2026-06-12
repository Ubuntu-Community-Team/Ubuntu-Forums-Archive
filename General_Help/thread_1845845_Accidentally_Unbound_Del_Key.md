---
title: "Accidentally Unbound Del Key"
date: 2011-09-17
forum: General Help
---

### Post by thePowersGang on 2011-09-17
I was remapping keys last night using the Gnome Keyboard Shortcuts tool (gnome-keybinding-properties) and I think I managed to map an action to Delete. I removed the mapping, but now the delete key does not do anything in all applications (save for causing the cursor to blink).

I have done a bit of a search, and come across similar problems, but the solutions suggested did not work (due to being written for earlier versions of Ubuntu, I'm running 11.04)

A quick glance at the output of xev when I press the delete key seems to indicate that only a release event is delivered, with no press event.

```

$ xev
...
FocusOut event, serial 30, synthetic NO, window 0x3a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   4294967168 0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 30, synthetic NO, window 0x3a00001,
    root 0xaa, subw 0x0, time 104678659, (648,486), root:(1676,536),
    state 0x0, keycode 119 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False

```

---

### Post by Triblaze on 2011-09-17
I don't know much about it, but under system>preferences>keyboard (I assume you can just search "keyboard" in unity), under layouts, there is the option to "reset to defaults". I assume this would reset the functionality to the delete key to what it is supposed to be. However, I have no idea what effect this would have on other keybindings you've set, so I'm just throwing this out there, it'd be best to wait for someone with more knowledge on the subject before trying it, if at all.

---

