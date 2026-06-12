---
title: "Switching to virtual terminal causes PC to hang"
date: 2010-06-30
forum: General Help
---

### Post by archerxn on 2010-06-30
Hi all,

I'm using Lucid on a laptop with a core i5 processor and an ATI Mobility Radeon HD 5650 GPU. Whenever I try to change to a virtual terminal with Ctrl+Alt+F1/2/3/etc my computer seems to hang. I have to turn it off by holding down the power button. 

Would anyone be able to suggest how I could fix this issue?

The icons on my panel with "Applications, Places, System" become slightly discolored and garbled when this happens, if it's any help.

---

### Post by dino99 on 2010-06-30
check: system admin hardware driver: it need to be activated

and look for usefull errors logged into .xsession-errors (/home, ctrl+h to see it) and into: system admin logviewer

---

### Post by archerxn on 2010-06-30
Do you mean I need to activate the FLGRX driver?

I've tried that already, it didn't end well - after rebooting all I got was a black screen. So I reinstalled Ubuntu and didn't activate the proprietary drivers this time.

---

