---
title: "missing keys in 11.4"
date: 2011-07-10
forum: General Help
---

### Post by benwalburn on 2011-07-10
I just installed Ubuntu 11.4 on my dell inspiron, but am having some issues.
I am missing the "b" "n" and spacebar key. When I press them, nothing happens. Is there a fix for this somewhere in the settings?

Thank you

---

### Post by enimeizoo on 2011-07-12
Well, first thing to do is to check your keyboard layout. I can't really tell you where the option is since I'm using kde.

Another thing to try (if that doesn't work) is to see if the keys send events.
Useful softwares will be xev and xmodmap.

1) open a terminal and run 
```
xev
```A little white window should show up. You should then avoid clicking to keep the focus on the new window. 

2) Press some keys. You should see an output in the terminal where you ran xev. It should look like :
```

KeyPress event, serial 35, synthetic NO, window 0x6000001,
    root 0xa8, subw 0x0, time 22908422, (66,375), root:(788,398),
    state 0x10, keycode 65 (keysym 0x20, space), same_screen YES,
    XLookupString gives 1 bytes: (20) " "
    XmbLookupString gives 1 bytes: (20) " "
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x6000001,
    root 0xa8, subw 0x0, time 22908523, (66,375), root:(788,398),
    state 0x10, keycode 65 (keysym 0x20, space), same_screen YES,
    XLookupString gives 1 bytes: (20) " "
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0x6000001,
    root 0xa8, subw 0x0, time 22909835, (66,375), root:(788,398),
    state 0x10, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: (78) "x"
    XmbLookupString gives 1 bytes: (78) "x"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x6000001,
    root 0xa8, subw 0x0, time 22909951, (66,375), root:(788,398),
    state 0x10, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: (78) "x"
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0x6000001,
    root 0xa8, subw 0x0, time 22910347, (66,375), root:(788,398),
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    XLookupString gives 1 bytes: (68) "h"
    XmbLookupString gives 1 bytes: (68) "h"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x6000001,
    root 0xa8, subw 0x0, time 22910452, (66,375), root:(788,398),
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    XLookupString gives 1 bytes: (68) "h"
    XFilterEvent returns: False


```(2 events by keypress, I pressed space, then x, then h)
See if events appear when you press your keys. If it does, it should be pretty easy to fix.

3) when you're done and have some output to post here, you can just close the little white window.

4) if you get events for your keys, you can try to map them via xmodmap.

Hope it helps. But there are a lot of ifs, so don't hesitate to post back here if something goes wrong.

---

### Post by seawolf167 on 2011-07-12
As previously posted - check you keyboard layout to ensure you have the correct one selected.

Next thing - are you sure the keyboard works alright? Have you tried it in another computer or OS?

---

