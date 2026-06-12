---
title: "Find Desktop Coordinates"
date: 2009-11-30
forum: General Help
---

### Post by Hesediel on 2009-11-30
I would like to find desktop coordinates, for example: x,y for positionate my text in my conkyrc..

---

### Post by sisco311 on 2009-11-30
run
```
xev
```
and drag the *Event Tester* window.

The position of the window is enclosed in parentheses:
```
ConfigureNotify event, serial 34, synthetic YES, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, **(708,355)**, width 272, height 240,
    border_width 0, above 0x113b579, override NO
```

---

### Post by Hesediel on 2009-11-30
Thank you... great as always guys.

---

