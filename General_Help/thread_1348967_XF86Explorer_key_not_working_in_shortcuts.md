---
title: "XF86Explorer key not working in shortcuts"
date: 2009-12-07
forum: General Help
---

### Post by OrangeVixen on 2009-12-07
I'm trying to set the XF86Explorer key in System->Preferences->Keyboard Shortcuts to a custom command (the command in case to call gnome-screensaver-command to blank the screen.

I have it calling a script which has a sleep 1 so that the keyrelease does not deactivate it.

But the problem is that when I press the XF86Explorer key, nothing happens. I tried having it call another command, like gedit, nothing. To make sure that key was working I used xev, and yes it was:

KeyPress event, serial 37, synthetic NO, window 0x3600001,
    root 0x13c, subw 0x0, time 169163000, (166,2), root:(173,517),
    state 0x10, keycode 152 (keysym 0x1008ff5d, XF86Explorer), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

I tried mapping my script to any key other than XF86Explorer and it does work! so why is it that XF86Explorer key does not work in shortcuts?

---

