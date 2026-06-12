---
title: "Remap mouse buttons to keyboard"
date: 2010-06-12
forum: General Help
---

### Post by TheDesertDragon on 2010-06-12
When I play games on my Windows computer, I've remapped the mouse wheel tilts on my Logitech G5 (using SetPoint) to " for tilt-left and ' for tilt-right. This facilitates being able to use the buttons in games, which are really useful, but which normally is not supported by any program.

Wine remaps them to mouse scrolling, which really, really sucks, and I can't for the life of me figure out how to change it. (I've figured out switching around mouse buttons and keyboard buttons using xmodmap, but I can't cross the border)

Anyone knows how to do this?

EDIT:
Almost got it working, but it's behaving really erratically.

Here's how:

sudo apt-get install xbindkeys xbindkeys-config xautomate
xbindkeys

Create a new shortcut - for example:
b:6
Run the following command:
xte 'keydown Contrl_L' 'key P' keyup Control_L'

That will make b:6 behave like Ctrl+P.

However, it doesn't make any other key at the same time as b:6 work as that key plus Ctrl+P.
In order words, all keys plus b:6 will return they key pressed and b:6, which is not want I wanted. I wanted the b:6 mod to be completely persistant through all possible combinations.

Is this even possible?

---

### Post by TheDesertDragon on 2010-06-13
Bump

---

### Post by TheDesertDragon on 2010-06-14
Bump again!

---

### Post by TheDesertDragon on 2010-06-14
Is this really impossible?

---

### Post by TheDesertDragon on 2010-06-14
If it is then I will probably quit using Ubuntu for all gaming and put back W7 on my laptop - which would suck because overall I really prefer Ubuntu.

---

