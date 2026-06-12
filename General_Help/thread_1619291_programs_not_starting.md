---
title: "programs not starting"
date: 2010-11-11
forum: General Help
---

### Post by claudehopper on 2010-11-11
When clicking on a program to start from the drop down menu (latest example being Quadrapassel) the program starts but then the tab at the bottom of the screen disappears and the program doesn't load.

any solution to this?:confused:

---

### Post by lisati on 2010-11-11
Isn't it a nuisance when there is no sign of an error message when a program stops for no apparent reason?

What might be helpful for us is if you are able to start the program from the command line (Applications->Accessories->Terminal) and reply here with any error messages you see.

---

### Post by Vigh on 2010-11-11
did you do anything with loading old un-supported libraries? i had the same problem, i had loaded old python 2.4 and GTK1.2 which seemed to break some application launchers, I solved this by finding a better way to run the old apps I needed (Wine/Virtual Machine)  and just using the current versions of python and GTK

---

### Post by gregwm on 2010-11-15
+1
(lubuntu lucid)
from bash:
quadrapassel
Failed to initialise clutter: Unable to find suitable fbconfig for the GLX context

---

### Post by gregwm on 2010-11-15
see
[https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/564748](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/564748)

---

