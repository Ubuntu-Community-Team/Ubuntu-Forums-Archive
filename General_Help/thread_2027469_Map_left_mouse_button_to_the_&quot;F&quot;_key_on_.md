---
title: "Map left mouse button to the &quot;F&quot; key on keyboard"
date: 2012-07-16
forum: General Help
---

### Post by jaceguay on 2012-07-16
Hi, in windows I use to have autohotkey to do this but on ubuntu I have no clue on how to map the left mouse button to the F key on keyboard.

---

### Post by jaceguay on 2012-07-18
Here is what I´ve try:

xmodmap -e "keycode 41 = Pointer_Button1"

but nothing happen, 
if i use :

xmodmap -e "keycode 41 = KP_5"

and turn universal access/Mouse Keys on, it work as intended, but I lost the other keypad buttons as now they are simulating the mouse.
Maybe this is the only way, but someone know if xmodmap can really simulate the mouse button?

---

