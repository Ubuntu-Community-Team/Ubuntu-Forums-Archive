---
title: "Problem with HD4870 Dual Display"
date: 2010-01-08
forum: General Help
---

### Post by Rob_G on 2010-01-08
Hi I am new to ubuntu and am having major problems setting my displays up. my setup is a hd TV to the Left of my pc monitor, i have managed to configure catalyst to let me have a main display with the second display being an extension of the first, the problem is i cannot seem to swap my primary display, at the minute my HDTV has all the taskbars and everything on it while my pc monitor is just a blank background, i would like it so i could start a film playing for my children, then drag it across to the HDTV while i can still use my pc in the background please can anyone help with this as it has been doing my head in all day!! Thanks in advance.

---

### Post by Rob_G on 2010-01-09
anyone have any ideas? if i can't solve it i think ubuntu is going in the bin and i will stick with windows 7

---

### Post by waerna on 2012-03-25
what worked for me was:

set up a new startup application (System - Preferences - Startup application) which just does:
xrandr --output DFP4 --primary
DFP4 is the name of my primary display

---

