---
title: "Cannot type a capital &quot;m&quot;   !????"
date: 2010-12-04
forum: General Help
---

### Post by realzippy on 2010-12-04
Sick of avoiding capital "m" in my computer usage I decided to buy a new keyboard at last;big surprise (ok,was wondering why "m" works,"shift" works,but not "shift + m" earlier,but needed a new keyboard anyway):
problem persist with the new keyboard.
Tried different keyboard layouts,fonts,nothing.,still can not type "M"..
..had to copy&paste this wonderful big one   ;-)

This is on maverick32;booting lucid64 all is fine...
....must be gnome-related,the shell is fine also.
Where do I start searching for my "blacklisted" "shift + m"  ?
Any ideas?

---

### Post by karthick87 on 2010-12-04
Goto** System>>Preferences>>Keyboard Shortcuts** and see whether you have assigned SHIFT+M as a shorcut cut for something else.

---

### Post by WorMzy on 2010-12-04
Can you open a terminal and run xev, then press Shift+M and see what the terminal output is. Here's mine for comparison

```
KeyPress event, serial 35, synthetic NO, window 0x4800001,
    root 0x15a, subw 0x0, time 8099967, (474,51), root:(521,550),
    state 0x11, keycode 58 (keysym 0x4d, M), same_screen YES,
    XLookupString gives 1 bytes: (4d) "M"
    XmbLookupString gives 1 bytes: (4d) "M"
    XFilterEvent returns: False
```

---

### Post by realzippy on 2010-12-04
Thanks karthick87,that idea helped:
It is not a gnome shortcut,but your idea made me switching from compiz to metacity,and I have back my "M".MMMMMMMMMMMMMMMMM.love it  ;-)
So I guess it is a compiz shortcut,will see if there is a general shortcut list...

---

### Post by realzippy on 2010-12-04
@WorMzy

...my xev output is the same,so input seems to work.

---

### Post by karthick87 on 2010-12-04
Glad it worked :)

---

### Post by WorMzy on 2010-12-04
Looks like you've isolated the problem, so my suggestion is superfluous anyway. :)

---

### Post by realzippy on 2010-12-04
Edit:

The compiz **M**aximumize plugin..
....*initiate* was set to shift+M instead of super+M.
Thanks you both for fast help!

---

### Post by Spyderkid on 2010-12-04
keyboard settings before you log in?

---

