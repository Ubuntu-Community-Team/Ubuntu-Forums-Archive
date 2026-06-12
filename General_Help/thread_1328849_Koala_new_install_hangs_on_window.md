---
title: "Koala new install hangs on window"
date: 2009-11-16
forum: General Help
---

### Post by Kaicias on 2009-11-16
I installed 9.10, and it hangs everytime i tried to open a window. I disabled compiz and it works fine - i just didn't have the top line of any window!
Once I re-enabled compiz, same hang!
Is there another window manager that doesn't hang 9.10?
Or is there a way to go back to 8.10 without losing everything?

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
type ```
metacity --replace
``` in the terminal and see what it looks like.

---

### Post by Kaicias on 2009-11-16
When the
metacity --replace
was entered the terminal screen just hangs, how long does it take?

---

### Post by Kaicias on 2009-11-16
I have also noticed a problem with my language support...a row of boxes show up on some drop down menu's

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
Should happen immediately. The terminal will hang without an & after the command but your windows should change regardless. Press ctrl+c and then type ```
metacity --replace &
``` this time and then check your window manager for the aforementioned problems. All this does is switch the manager from compiz to metacity and will disable desktop effects. If you want to switch back and forth 'compiz --replace' is the command to go back.

---

