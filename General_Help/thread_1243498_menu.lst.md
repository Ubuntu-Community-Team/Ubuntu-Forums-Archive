---
title: "menu.lst"
date: 2009-08-18
forum: General Help
---

### Post by jtmedin on 2009-08-18
Would someone explain this please. I bring up menu.lst & change: 
default		saved
#default		6

near the top. Then i add savedefault to the following:
title		Windows Vista (loader)
rootnoverify	(hd0,0)
makeactive
chainloader	+1
savedefault

near the end. But the boot doesn't default to the 'Windows Vista (loader)'. i have tried all kinds of combos but no banana.


HELP

---

### Post by mcduck on 2009-08-18
Try putting the "savedefault" above the "makeactive" and "chainloader +1". That should work. If you boot into Windows it should do the same automatically on the next boot.

(it's too late to try to save the default setting after you've already given the control to the Windows bootloader.)

---

### Post by Dakiraun on 2009-08-18
The count begins at 0 - make sure you're not one off.

---

### Post by jtmedin on 2009-08-18
> **mcduck said:**
> Try putting the "savedefault" above the "makeactive" and "chainloader +1". That should work. If you boot into Windows it should do the same automatically on the next boot.

(it's too late to try to save the default setting after you've already given the control to the Windows bootloader.)
No that doesnt work. Tried it :-(.

---

### Post by mcduck on 2009-08-18
> **jtmedin said:**
> No that doesnt work. Tried it :-(.

Keep in mind that that setting won't set Windows to *always* be the default entry. It only means that if you now select Windows manually, it will be the default on *next* boot.

If you want the Windows entry to always be the default you need to use the number, not "saved".

---

### Post by jtmedin on 2009-08-20
Ah thats the key thanks!

---

