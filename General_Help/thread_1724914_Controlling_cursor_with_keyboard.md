---
title: "Controlling cursor with keyboard"
date: 2011-04-08
forum: General Help
---

### Post by josephellengar on 2011-04-08
Gnome, 10.10 (likely not to upgrade to 11.04), HP-dv7t laptop, intel i7 processor

In my ongoing attempt to create a completely mouseless computing experience (and hopefully, one where I never have to leave the home row) I am currently trying to find a way to control the onscreen cursor with my keyboard. 

I have found various solutions, but most of them have problems. The accessibility feature that comes with Ubuntu is (for some reason) not installed on my computer and I can't find the package, but other people who have tried the same thing have said that it is not worth the effort anyway, given that it has nonexistent customization.

This shift-numlock function doesn't work at all.

Got info from this thread: ubuntuforums.org/showthread.php?t=926105

Gizmod is incredibly complex and doesn't seem to work all that well with my 64 bit hardware. I worked with it for a few hours.

But, anyway, do you have any advice that has not already been posted in the other thread?  Thanks.

---

### Post by Krytarik on 2011-04-09
When you go to "System -> Preferences -> Keyboard -> Mouse Keys", you should be able to activate/configure those feature.

Do you have a num-keypad at your laptop, that you can comfortably use for that?
Or do you want to remap those keys to different ones?

Greetings.

---

### Post by josephellengar on 2011-04-09
> **Krytarik said:**
> When you go to "System -> Preferences -> Keyboard -> Mouse Keys", you should be able to activate/configure those feature.

Do you have a num-keypad at your laptop, that you can comfortably use for that?
Or do you want to remap those keys to different ones?

Greetings.

Thanks. But how do I click with that? I do have a num-keypad on my laptop and it seems to be working, though it is a little laggy (even when I set it to high speed).

Also, I was hoping to remap so that I could use some hotkey+keys on the home row to move the cursor/click so I wouldn't have to move my hand.

---

### Post by Krytarik on 2011-04-09
> **josephellengar said:**
> Thanks. But how do I click with that?It's the key with the number "5", usually in the middle of a numkey-pad.
> **josephellengar said:**
> 
Also, I was hoping to remap so that I could use some hotkey+keys on the home row to move the cursor/click so I wouldn't have to move my hand.
Then simply say what keys you would like to remap to what, and even better, check with```
xev
```what "keycodes" and "keysyms" the concerning keys have, because it *might* be different at your keyboard, just to be sure. Simply run the command, then press the concerning keys, close the upcoming window to quit.

---

### Post by josephellengar on 2011-04-09
> **Krytarik said:**
> It's the key with the number "5", usually in the middle of a numkey-pad.

Then simply say what keys you would like to remap to what, and even better, check with```
xev
```what "keycodes" and "keysyms" the concerning keys have, because it *might* be different at your keyboard, just to be sure. Simply run the command, then press the concerning keys, close the upcoming window to quit.

Okay, I'd like to remap caps-lock-j to left, caps-lock-i to up, caps-lock-l to right, caps-lock-m to down, and caps-lock-k to click. Thanks for your help with the numpad. I was able to get that to work. Here is the xev output for those keys. (Capslock is remapped to backspace right now, but I was never able to get used to using it. That's why I have that instead of capslock.)

```


MotionNotify event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 689708, (78,85), root:(778,135),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 689716, (79,84), root:(779,134),
    state 0x10, is_hint 0, same_screen YES

KeyPress event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 691925, (79,84), root:(779,134),
    state 0x10, keycode 31 (keysym 0x69, i), same_screen YES,
    XLookupString gives 1 bytes: (69) "i"
    XmbLookupString gives 1 bytes: (69) "i"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 692102, (79,84), root:(779,134),
    state 0x10, keycode 31 (keysym 0x69, i), same_screen YES,
    XLookupString gives 1 bytes: (69) "i"
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 693503, (79,84), root:(779,134),
    state 0x10, keycode 44 (keysym 0x6a, j), same_screen YES,
    XLookupString gives 1 bytes: (6a) "j"
    XmbLookupString gives 1 bytes: (6a) "j"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 693606, (79,84), root:(779,134),
    state 0x10, keycode 44 (keysym 0x6a, j), same_screen YES,
    XLookupString gives 1 bytes: (6a) "j"
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 694595, (79,84), root:(779,134),
    state 0x10, keycode 45 (keysym 0x6b, k), same_screen YES,
    XLookupString gives 1 bytes: (6b) "k"
    XmbLookupString gives 1 bytes: (6b) "k"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 694700, (79,84), root:(779,134),
    state 0x10, keycode 45 (keysym 0x6b, k), same_screen YES,
    XLookupString gives 1 bytes: (6b) "k"
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 695587, (79,84), root:(779,134),
    state 0x10, keycode 46 (keysym 0x6c, l), same_screen YES,
    XLookupString gives 1 bytes: (6c) "l"
    XmbLookupString gives 1 bytes: (6c) "l"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 695763, (79,84), root:(779,134),
    state 0x10, keycode 46 (keysym 0x6c, l), same_screen YES,
    XLookupString gives 1 bytes: (6c) "l"
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 696875, (79,84), root:(779,134),
    state 0x10, keycode 58 (keysym 0x6d, m), same_screen YES,
    XLookupString gives 1 bytes: (6d) "m"
    XmbLookupString gives 1 bytes: (6d) "m"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 696989, (79,84), root:(779,134),
    state 0x10, keycode 58 (keysym 0x6d, m), same_screen YES,
    XLookupString gives 1 bytes: (6d) "m"
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 697549, (79,84), root:(779,134),
    state 0x10, keycode 66 (keysym 0xff08, BackSpace), same_screen YES,
    XKeysymToKeycode returns keycode: 22
    XLookupString gives 1 bytes: (08) "
    XmbLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 697688, (79,84), root:(779,134),
    state 0x10, keycode 66 (keysym 0xff08, BackSpace), same_screen YES,
    XKeysymToKeycode returns keycode: 22
    XLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

```

EDITED TO ADD: Also, how do I right-click using the keypad?
EDITED TO ADD: I'd like to make right-click capslock-semicolon, but I can probably figure that out if you just explain how I go about remapping the rest of the stuff that I mentioned.

Thank you!

---

### Post by Krytarik on 2011-04-09
Ok, this seems to get a lot trickier than I was hoping ;-), because mapping a key's keysym to another key's keysym for a custom modifier seems not to be possible with xmodmap. I did a lot of fiddling/testing just yet.

In the meanwhile please do same "xev" lookup for the usual numkeys.

Regarding the right-click, there seems to be no way to do just a *single* right-click, at least not without tweaking, which we are planning to do anyway. To switch the function of numkey "5" between left- and right-click, one has usually to use the
- numkeys "/" and "*" to enable left-click
- numkey "-" to enable right-click.

---

### Post by josephellengar on 2011-04-09
> **Krytarik said:**
> Ok, this seems to get a lot trickier than I was hoping ;-), because mapping a key's keysym to another key's keysym for a custom modifier seems not to be possible with xmodmap. I did a lot of fiddling/testing just yet.

In the meanwhile please do same "xev" lookup for the usual numkeys.

Regarding the right-click, there seems to be no way to do just a *single* right-click, at least not without tweaking, which we are planning to do anyway. To switch the function of numkey "5" between left- and right-click, one has usually to use the
- numkeys "/" and "*" to enable left-click
- numkey "-" to enable right-click.

Ooh, that worked perfectly. Thanks!
Here is the xev output of my numpad:

```

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 494631, (78,100), root:(735,103),
    state 0x10, keycode 87 (keysym 0xffb1, KP_1), same_screen YES,
    XLookupString gives 1 bytes: (31) "1"
    XmbLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 494699, (78,100), root:(735,103),
    state 0x10, keycode 87 (keysym 0xffb1, KP_1), same_screen YES,
    XLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 495549, (78,100), root:(735,103),
    state 0x10, keycode 88 (keysym 0xffb2, KP_2), same_screen YES,
    XLookupString gives 1 bytes: (32) "2"
    XmbLookupString gives 1 bytes: (32) "2"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 495688, (78,100), root:(735,103),
    state 0x10, keycode 88 (keysym 0xffb2, KP_2), same_screen YES,
    XLookupString gives 1 bytes: (32) "2"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 496073, (78,100), root:(735,103),
    state 0x10, keycode 89 (keysym 0xffb3, KP_3), same_screen YES,
    XLookupString gives 1 bytes: (33) "3"
    XmbLookupString gives 1 bytes: (33) "3"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 496212, (78,100), root:(735,103),
    state 0x10, keycode 89 (keysym 0xffb3, KP_3), same_screen YES,
    XLookupString gives 1 bytes: (33) "3"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 496566, (78,100), root:(735,103),
    state 0x10, keycode 83 (keysym 0xffb4, KP_4), same_screen YES,
    XLookupString gives 1 bytes: (34) "4"
    XmbLookupString gives 1 bytes: (34) "4"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 496669, (78,100), root:(735,103),
    state 0x10, keycode 83 (keysym 0xffb4, KP_4), same_screen YES,
    XLookupString gives 1 bytes: (34) "4"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 497005, (78,100), root:(735,103),
    state 0x10, keycode 84 (keysym 0xffb5, KP_5), same_screen YES,
    XLookupString gives 1 bytes: (35) "5"
    XmbLookupString gives 1 bytes: (35) "5"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 497146, (78,100), root:(735,103),
    state 0x10, keycode 84 (keysym 0xffb5, KP_5), same_screen YES,
    XLookupString gives 1 bytes: (35) "5"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 497377, (78,100), root:(735,103),
    state 0x10, keycode 85 (keysym 0xffb6, KP_6), same_screen YES,
    XLookupString gives 1 bytes: (36) "6"
    XmbLookupString gives 1 bytes: (36) "6"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 497517, (78,100), root:(735,103),
    state 0x10, keycode 85 (keysym 0xffb6, KP_6), same_screen YES,
    XLookupString gives 1 bytes: (36) "6"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 497765, (78,100), root:(735,103),
    state 0x10, keycode 79 (keysym 0xffb7, KP_7), same_screen YES,
    XLookupString gives 1 bytes: (37) "7"
    XmbLookupString gives 1 bytes: (37) "7"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 497870, (78,100), root:(735,103),
    state 0x10, keycode 79 (keysym 0xffb7, KP_7), same_screen YES,
    XLookupString gives 1 bytes: (37) "7"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 498100, (78,100), root:(735,103),
    state 0x10, keycode 80 (keysym 0xffb8, KP_8), same_screen YES,
    XLookupString gives 1 bytes: (38) "8"
    XmbLookupString gives 1 bytes: (38) "8"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 498241, (78,100), root:(735,103),
    state 0x10, keycode 80 (keysym 0xffb8, KP_8), same_screen YES,
    XLookupString gives 1 bytes: (38) "8"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 498475, (78,100), root:(735,103),
    state 0x10, keycode 81 (keysym 0xffb9, KP_9), same_screen YES,
    XLookupString gives 1 bytes: (39) "9"
    XmbLookupString gives 1 bytes: (39) "9"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 498577, (78,100), root:(735,103),
    state 0x10, keycode 81 (keysym 0xffb9, KP_9), same_screen YES,
    XLookupString gives 1 bytes: (39) "9"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 499865, (78,100), root:(735,103),
    state 0x10, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 32, synthetic NO, window 0x4c00001,
    atom 0x18e (XKLAVIER_STATE), time 499867, state PropertyNewValue

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 499972, (78,100), root:(735,103),
    state 0x10, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 501615, (78,100), root:(735,103),
    state 0x0, keycode 87 (keysym 0xff9c, KP_End), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 501720, (78,100), root:(735,103),
    state 0x0, keycode 87 (keysym 0xff9c, KP_End), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 502193, (78,100), root:(735,103),
    state 0x0, keycode 88 (keysym 0xff99, KP_Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 502334, (78,100), root:(735,103),
    state 0x0, keycode 88 (keysym 0xff99, KP_Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 502681, (78,100), root:(735,103),
    state 0x0, keycode 89 (keysym 0xff9b, KP_Next), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 502787, (78,100), root:(735,103),
    state 0x0, keycode 89 (keysym 0xff9b, KP_Next), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 503247, (78,100), root:(735,103),
    state 0x0, keycode 83 (keysym 0xff96, KP_Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 503354, (78,100), root:(735,103),
    state 0x0, keycode 83 (keysym 0xff96, KP_Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 503667, (78,100), root:(735,103),
    state 0x0, keycode 84 (keysym 0xff9d, KP_Begin), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 503806, (78,100), root:(735,103),
    state 0x0, keycode 84 (keysym 0xff9d, KP_Begin), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 504041, (78,100), root:(735,103),
    state 0x0, keycode 85 (keysym 0xff98, KP_Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 504182, (78,100), root:(735,103),
    state 0x0, keycode 85 (keysym 0xff98, KP_Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 504489, (78,100), root:(735,103),
    state 0x0, keycode 79 (keysym 0xff95, KP_Home), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 504592, (78,100), root:(735,103),
    state 0x0, keycode 79 (keysym 0xff95, KP_Home), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 504754, (78,100), root:(735,103),
    state 0x0, keycode 80 (keysym 0xff97, KP_Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 504893, (78,100), root:(735,103),
    state 0x0, keycode 80 (keysym 0xff97, KP_Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 505058, (78,100), root:(735,103),
    state 0x0, keycode 81 (keysym 0xff9a, KP_Prior), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 505198, (78,100), root:(735,103),
    state 0x0, keycode 81 (keysym 0xff9a, KP_Prior), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 508620, (78,100), root:(735,103),
    state 0x0, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 32, synthetic NO, window 0x4c00001,
    atom 0x18e (XKLAVIER_STATE), time 508622, state PropertyNewValue

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 508689, (78,100), root:(735,103),
    state 0x10, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 518155, (78,100), root:(735,103),
    state 0x10, keycode 106 (keysym 0xffaf, KP_Divide), same_screen YES,
    XLookupString gives 1 bytes: (2f) "/"
    XmbLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 518366, (78,100), root:(735,103),
    state 0x10, keycode 106 (keysym 0xffaf, KP_Divide), same_screen YES,
    XLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 518604, (78,100), root:(735,103),
    state 0x10, keycode 63 (keysym 0xffaa, KP_Multiply), same_screen YES,
    XLookupString gives 1 bytes: (2a) "*"
    XmbLookupString gives 1 bytes: (2a) "*"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 518778, (78,100), root:(735,103),
    state 0x10, keycode 63 (keysym 0xffaa, KP_Multiply), same_screen YES,
    XLookupString gives 1 bytes: (2a) "*"
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 519236, (78,100), root:(735,103),
    state 0x10, keycode 82 (keysym 0xffad, KP_Subtract), same_screen YES,
    XLookupString gives 1 bytes: (2d) "-"
    XmbLookupString gives 1 bytes: (2d) "-"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 519340, (78,100), root:(735,103),
    state 0x10, keycode 82 (keysym 0xffad, KP_Subtract), same_screen YES,
    XLookupString gives 1 bytes: (2d) "-"
    XFilterEvent returns: False


```

---

### Post by Krytarik on 2011-04-11
Just so that you know, I'm still working on this, but obviously, I can't do this nonstop, not at least because it tends to become really frustrating after a while. ;-)

But I feel that I'm progressing towards the target, yesterday I've figured why xmodmap doesn't have the effect like the manpage states, and how to modify the command options to match the current realities. However, I still have to figure how to apply a custom modifier and the respective keysyms to specific keys.

In the meanwhile please post the "xev" output of your semicolon key, and the outputs of these commands:```

xmodmap -pm
xmodmap -pk |egrep " 31 | 44 | 45 | 46 | 58 | <keycode-of-semicolon> "
```

---

### Post by josephellengar on 2011-04-11
> **Krytarik said:**
> Just so that you know, I'm still working on this, but obviously, I can't do this nonstop, not at least because it tends to become really frustrating after a while. ;-)

But I feel that I'm progressing towards the target, yesterday I've figured why xmodmap doesn't have the effect like the manpage states, and how to modify the command options to match the current realities. However, I still have to figure how to apply a custom modifier and the respective keysyms to specific keys.

In the meanwhile please post the "xev" output of your semicolon key, and the outputs of these commands:```

xmodmap -pm
xmodmap -pk |egrep " 31 | 44 | 45 | 46 | 58 | <keycode-of-semicolon> "
```

Thank you very much. It's no problem at all. I appreciate your time.

Here is the output you asked for:

```

KeyPress event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 163155, (76,104), root:(1388,154),
    state 0x0, keycode 47 (keysym 0x3b, semicolon), same_screen YES,
    XLookupString gives 1 bytes: (3b) ";"
    XmbLookupString gives 1 bytes: (3b) ";"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 163226, (76,104), root:(1388,154),
    state 0x0, keycode 47 (keysym 0x3b, semicolon), same_screen YES,
    XLookupString gives 1 bytes: (3b) ";"
    XFilterEvent returns: False

```
```

ross@ross-laptop:~$ xmodmap -pm
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock      
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x42),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

```
```

ross@ross-laptop:~$ xmodmap -pk |egrep " 31 | 44 | 45 | 46 | 58 | <47> "
     31    	0x0069 (i)	0x0049 (I)	0x0069 (i)	0x0049 (I)	
     44    	0x006a (j)	0x004a (J)	0x006a (j)	0x004a (J)	
     45    	0x006b (k)	0x004b (K)	0x006b (k)	0x004b (K)	
     46    	0x006c (l)	0x004c (L)	0x006c (l)	0x004c (L)	
     58    	0x006d (m)	0x004d (M)	0x006d (m)	0x004d (M)	

```

---

### Post by Krytarik on 2011-04-11
> **josephellengar said:**
> ```

ross@ross-laptop:~$ xmodmap -pk |egrep " 31 | 44 | 45 | 46 | 58 | <47> "
     31        0x0069 (i)    0x0049 (I)    0x0069 (i)    0x0049 (I)    
     44        0x006a (j)    0x004a (J)    0x006a (j)    0x004a (J)    
     45        0x006b (k)    0x004b (K)    0x006b (k)    0x004b (K)    
     46        0x006c (l)    0x004c (L)    0x006c (l)    0x004c (L)    
     58        0x006d (m)    0x004d (M)    0x006d (m)    0x004d (M)    

```
Is that really all!? I have some more keysyms assigned to those keys! Also, spare "<" and ">". ;)

---

### Post by josephellengar on 2011-04-11
> **Krytarik said:**
> Is that really all!? I have some more keysyms assigned to those keys! Also, spare "<" and ">". ;)

This might be better:

```

ross@ross-laptop:~$ xmodmap -pk |egrep " 31 | 44 | 45 | 46 | 58 | 47"
     31    	0x0069 (i)	0x0049 (I)	0x0069 (i)	0x0049 (I)	
     44    	0x006a (j)	0x004a (J)	0x006a (j)	0x004a (J)	
     45    	0x006b (k)	0x004b (K)	0x006b (k)	0x004b (K)	
     46    	0x006c (l)	0x004c (L)	0x006c (l)	0x004c (L)	
     47    	0x003b (semicolon)	0x003a (colon)	0x003b (semicolon)	0x003a (colon)	
     58    	0x006d (m)	0x004d (M)	0x006d (m)	0x004d (M)	

```

---

### Post by Krytarik on 2011-04-11
Ok, cool, since all of those keys apparently have no keysyms for AltGr/Mode_Switch assigned to them, I can simply use their places. It's going to be much easier now!

---

### Post by Felson on 2011-04-12
I am looking for the same kind of information.
I ran across this thread
[http://ubuntuforums.org/showthread.php?p=9666475](http://ubuntuforums.org/showthread.php?p=9666475)
that does it a slightly different way. I thought it might be of interest since it doesn't require remapping what keys do.

My issue is that I have a keyboard that has no Numlock key or number pad. Not even as a function key.

Perfect world, I would be able to use the arrow keys, Right Alt and Right Shift while holding down the windows logo key, and no need to toggle into the "mode" just have it on all the time.
That thread I posted as a link looks good, except that I have no idea how I would make it work with key-combos.

---

### Post by Krytarik on 2011-04-12
Thanks for joining us. I ran across your own thread earlier, but it wasn't really clear what exact mapping you want to achieve, and I was already busy with this one.
> **Felson said:**
> 
I ran across this thread
[http://ubuntuforums.org/showthread.php?p=9666475](http://ubuntuforums.org/showthread.php?p=9666475)
that does it a slightly different way. I thought it might be of interest since it doesn't require remapping what keys do.

The downside of those setup is that
- it doesn't support the acceleration feature of the built-in Mouse Keys
- it is hardware specific.

But now I know at least the keysym to activate Mouse Keys!

That really helps in your case, we can simply activate it with a command in "Startup Applications".

Please hold on, I have first to finish this one, then I will turn to your own thread. But I'm a bit short of time/passion right now.

@josephenllengar: The other thread reminded me of the keys for diagonal movements, we obviously didn't mind those. If you want to use them as well, please run the same commands on them, too, and post their outputs.

---

### Post by Krytarik on 2011-04-14
What about the keys for diagonal movements now?

---

### Post by josephellengar on 2011-04-14
> **Krytarik said:**
> What about the keys for diagonal movements now?

Oh, sorry I didn't get back to you earlier. I haven't checked my email for a few days. I don't think I need keys for diagonal movements. But thanks you. Once you explain how to remap the ones we discussed I'll probably be able to figure out how to remap the other ones to diagonal if I need to in the future.

---

### Post by Krytarik on 2011-04-14
Ok then, here is the solution:

- Set "System -> Preferences -> Keyboard -> Layout -> Options -> CapsLock key behavior" to "CapsLock is disabled"

- Create a file called ".Xmodmap" at the toplevel of your home directory, with those content:

~/.Xmodmap:```

keycode 66 = Caps_Lock
add mod5 = Caps_Lock
keycode 31 = i I i I KP_8
keycode 44 = j J j J KP_4
keycode 45 = k K k K KP_5
keycode 46 = l L l L KP_6
keycode 58 = m M m M KP_2
```[INDENT]As a side-effect, you can use CapsLock as an additional AltGr then.

The next time you login, you will most probably be asked if you want to   use the newly created Xmodmap file*, then just choose "Add" and confirm  with "OK".

*depends on if you had such a file before, and did already confirm/disable those query
[/INDENT]** To assign the semicolon key to the right-click:**

- Make sure that the package "xdotool" is installed, it's in the official repos.
- Add a keyboard shortcut in "System -> Preferences -> Keyboard Shortcuts" with this command:
```
sh -c "xdotool keyup Caps_Lock semicolon; xdotool click 3"
```- Assign the key combinition CapsLock+semicolon to it (yeah, it doesn't look like this, eventually).

** To enable Mouse Keys at startup:**

- Add a command like this to "System -> Preferences -> Startup Applications":
```
sh -c "sleep 13; xdotool key Pointer_EnableKeys"
```[INDENT]You need to adjust the delay (seconds) to your system, so that the actual command is only run when the desktop is already loaded.
[/INDENT]- Add this to your "~/.Xmodmap", so that the keypad still works like normal even if Mouse Keys is enabled:
```
keycode  63 = asterisk
keycode  79 = 7
keycode  80 = 8
keycode  81 = 9
keycode  82 = minus
keycode  83 = 4
keycode  84 = 5
keycode  85 = 6
keycode  86 = plus
keycode  87 = 1
keycode  88 = 2
keycode  89 = 3
keycode  90 = 0
keycode  91 = period
keycode 104 = Return
keycode 106 = slash
```[INDENT]Note that there will be no difference then if NumLock is enabled or not, may be an advantage, too.[/INDENT]

---

### Post by josephellengar on 2011-04-15
Oh, thanks! That worked perfectly! I just have one more question. I have been trying to set my right control key to be an extra super, but whenever I use the command 
```
 xmodmap -e 'keycode 105=Super_R' 
```
it instead changes my super key to be a control, which is a little odd. What's wrong with that command?

Here is my xev output:

```

KeyPress event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 1071574, (167,140), root:(1484,190),
    state 0x0, keycode 105 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 1071643, (167,140), root:(1484,190),
    state 0x4, keycode 105 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 1074931, (167,140), root:(1484,190),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XKeysymToKeycode returns keycode: 66
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4e00001,
    root 0x15d, subw 0x0, time 1075000, (167,140), root:(1484,190),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XKeysymToKeycode returns keycode: 66
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by Krytarik on 2011-04-15
It doesn't do exactly this at my system. But in any case, you need also to remove/re-add the concerning keysyms from/to the respective modifiers. So, add this to your "~/.Xmodmap":
```
remove control = Control_R
remove mod4 = Super_R
keycode 105 = Super_R
add mod4 = Super_R
```

---

