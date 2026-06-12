---
title: "Using the Super keys as Volume Up and Volume Down in Karmic possible?"
date: 2010-03-17
forum: General Help
---

### Post by susanne260 on 2010-03-17
Hi guys! :KS

In Intrepid Ibex, I was using the left Super key as Volume Down and the right Super key as Volume Up, because it was just so convenient.

However when I go to the "Keyboard Shortcuts" window in Karmic, it doesn't let me assign the Super keys to anything. I mean like, I can use the Super Keys along with other keys, but not by themselves.

Is it somehow possible to use the Super keys for Volume Up and Volume Down in Karmic? =)

---

### Post by JayUK20 on 2010-03-17
Sorry to jack the thread but i would also like to know how i could turn on/off wireless by using fn+f2

---

### Post by susanne260 on 2010-04-06
Ok, I've been using the following shortcuts In Karmic for the past two weeks:

Volume Down: LeftSuperKey+Z
Volume Up: LeftSuperKey+X

... and it has worked rather well so far. =)


However, if possible, I'd still like to use the following shortcuts instead. =D

Volume Down: LeftSuperKey
Volume Up: RightSuperKey

---

### Post by mikewhatever on 2010-04-06
What if you set the shortcuts a little differently. Run *gconf-editor*, navigate to /apps/gnome_settings_daemon/keybindings, find your volume related shortcuts, and change the value sections to *Super_L* and *Super_R* respectively.

---

