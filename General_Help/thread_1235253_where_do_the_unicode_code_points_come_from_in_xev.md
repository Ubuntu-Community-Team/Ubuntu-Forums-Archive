---
title: "where do the unicode code points come from in xev?"
date: 2009-08-08
forum: General Help
---

### Post by Dervin on 2009-08-08
Hello.
  When I hit "A" in the keyboard ```
xev
``` writes the following:
  ```
KeyPress event, serial 31, synthetic NO, window 0x2600001,
   root 0x59, subw 0x0, time 33208218, (-356,-157), root:(195,147),
   state 0x1, keycode 38 (keysym 0x41, A), same_screen YES,
   XLookupString gives 1 bytes: (41) "A"
   XmbLookupString gives 1 bytes: (41) "A"
   XFilterEvent returns: False
```  Could anyone tell me exactly where it translates the keycode 38 (which I know where to find) to the unicode codes in lines 3, 4, and 5?
  Thank you.

---

