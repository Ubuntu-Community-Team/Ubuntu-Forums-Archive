---
title: "Window buttons on left?"
date: 2010-06-12
forum: General Help
---

### Post by DThurman on 2010-06-12
I don't know why a decision was made to force the window
buttons (Close, Minimize, Maximize) on the left but it
is a major change from a standard that existed for a long
time. I guess the majority of Ubuntu users in the community
are lefties? :P

Someone on the Internet suggested that one can change window
button placement by:

Right Side
==========
Move Ubuntu desktop window control buttons to the right:
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "menu:minimize,maximize,close"

Left Side
=========
Switch back to desktop window control buttons to the left:
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"

But this is a temporary change, it is not permanent.  This
reverts back to default (left) once one changes the desktop
via  "Change Desktop Background"

How can I make this setting a system-wide default and permanently?

NOTE:
  You might notice that once the buttons are moved to the
  right side, there is left a single button on the left that
  does not seem to do anything special, it is just there!

---

### Post by DThurman on 2010-06-12
Ok, ok... I did not read the Sticky!  I see why now,
but geez, it's so hard to change!  Now I have to become
a lefty (and righty!)

---

