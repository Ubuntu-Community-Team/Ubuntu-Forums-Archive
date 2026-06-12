---
title: "function keys not working since upgrade to 11.10"
date: 2011-10-17
forum: General Help
---

### Post by roberto.tomas on 2011-10-17
since upgrading to 11.10 I've noticed that the ctl+alt+backspace and ctl+alt+fn keys arent working. I fixed the ctl+alt+backspace -- just changing the keyboard layout option worked. But the function keys to get to the consoles, I'm not sure how to fix. I'm pretty sure the problem is the function keys, because alt+f2 doesn't give me a command prompt either, and I have no custom keyboard shortcuts and that setting is still in System keyboard shortcuts

I *think* the problem is that the keyboard function keys aren't mapped properly any more.
xev output:
> <when I press F1>
KeyPress event, serial 36, synthetic NO, window 0x3e00001,
    root 0x1ad, subw 0x0, time 2580291, (-436,-111), root:(758,681),
    state 0x0, keycode 146 (keysym 0xff6a, Help), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3e00001,
    root 0x1ad, subw 0x0, time 2580443, (-436,-111), root:(758,681),
    state 0x0, keycode 146 (keysym 0xff6a, Help), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

<for F2>
KeyPress event, serial 36, synthetic NO, window 0x3e00001,
    root 0x1ad, subw 0x0, time 2601220, (-264,-75), root:(929,717),
    state 0x0, keycode 139 (keysym 0xff65, Undo), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3e00001,
    root 0x1ad, subw 0x0, time 2601340, (-264,-75), root:(929,717),
    state 0x0, keycode 139 (keysym 0xff65, Undo), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
those 0 bytes look like its not mapped correctly, yes? how can I get the console working? It *was* working when I was still on 11.04

---

### Post by roberto.tomas on 2011-10-17
:popcorn:I resolved this issue myself. It appears there was an issue with compiz, deleting the compiz temporary files and logging in again fixed the issue.

solution:
>  rm -rf .cache/compizconfig-1/* .compiz-1/* .config/compiz-1/*

---

