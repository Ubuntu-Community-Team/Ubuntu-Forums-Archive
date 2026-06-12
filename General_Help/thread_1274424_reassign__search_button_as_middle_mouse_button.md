---
title: "reassign  search button as middle mouse button"
date: 2009-09-24
forum: General Help
---

### Post by P4man on 2009-09-24
Hi,

I learned something new today; I already knew you can move a window without the window border by holding alt and dragging it. Now i read you can resize it holding alt and using the middle mouse button. Thats neat!

however, my middle mouse button is on the scroll wheel and quite difficult to use. I'd like to change that to the "search" button of my mouse (MX revolution). This search button, using xev generates a keypress  (keycode 225 and "XF86Search"). here is the xev output:
```

**KeyPress event**, serial 37, synthetic NO, window 0x4200001,
    root 0x1a7, subw 0x0, time 165303008, (119,90), root:(123,142),
    state 0x10, **keycode 225** (keysym 0x1008ff1b, **XF86Search**), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Id actually like that button to act as middle mouse  button everywhere (also in blender for instance). Any hints how I achieve that ? FWIW, this is the xev output for my actual middle mouse button:
```

**ButtonPress** event, serial 35, synthetic NO, window 0x4000001,
    root 0x1a7, subw 0x0, time 165384541, (48,90), root:(713,142),
    state 0x10, **button 2**, same_screen YES
```

---

### Post by P4man on 2009-09-25
bump

---

### Post by P4man on 2009-10-16
bumpy bump

---

### Post by P4man on 2009-10-23
**Almost solved** thanks to a tip by kanikilu
Here is the solution:
[http://ubuntuforums.org/showpost.php?p=6273040&postcount=2](http://ubuntuforums.org/showpost.php?p=6273040&postcount=2)

Just uncomment the last line and comment out the other xmodmap line and change the keycode to 225. Oh and change the first line if it doesnt match your keyboard.

**Problem is, this turns on mousekeys which in turn disables the numeric keyboard :(**

---

