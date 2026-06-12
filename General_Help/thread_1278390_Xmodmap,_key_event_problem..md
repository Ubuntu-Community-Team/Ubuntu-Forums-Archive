---
title: "Xmodmap, key event problem."
date: 2009-09-29
forum: General Help
---

### Post by Eltosch on 2009-09-29
Hi, I have a remote control that registers as two different HID devices which I can't get to fully work together with for example XBMC. The problem is that it generates multiple keys for many of the buttons on the remote.

I have tried several methods to get this to work, the latest experiment is to try to modify the xmodmap file, but I haven't succeded.

When running xev I get this output for one of the buttons , my first question is why the XmbLookupString doesn't recognize the same symbol on keypress/keyrelease?

KeyPress event, serial 36, synthetic NO, window 0x3600001,
    root 0x13f, subw 0x3600002, time 4677533, (47,53), root:(1148,130),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x3600001,
    root 0x13f, subw 0x3600002, time 4677533, (47,53), root:(1148,130),
    state 0x14, keycode 56 (keysym 0x62, b), same_screen YES,
    XLookupString gives 1 bytes: (02) ""
    XmbLookupString gives 1 bytes: (02) ""
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3600001,
    root 0x13f, subw 0x3600002, time 4677541, (47,53), root:(1148,130),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3600001,
    root 0x13f, subw 0x3600002, time 4677541, (47,53), root:(1148,130),
    state 0x10, keycode 56 (keysym 0x62, b), same_screen YES,
    XLookupString gives 1 bytes: (62) "b"
    XFilterEvent returns: False

Is it possible to get this keycombo to render a "b" on both the keypress and the keyrelease event?

One off the other buttons uses ctrl+shift+b, the same problem appears in that case, ideas?

Best regards
Tobias

---

### Post by Eltosch on 2009-10-05
Any ideas?
 
I'm stuck with this problem.
 
/Tobias

---

