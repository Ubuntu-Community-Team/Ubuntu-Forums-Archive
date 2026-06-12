---
title: "Keyboard &amp; Touchpad Don't work"
date: 2011-01-12
forum: General Help
---

### Post by deauvilleuk on 2011-01-12
Hi, recently whenever I start my laptop with Ubuntu Installed the startup screen goes strange (fuzzy/block type) then is fine when the desktop appears, but I can't use the touchpad or the keyboard.

Is there a repair option or does anyone know what has happened ?

Many thanks

Graham

---

### Post by acplusplusprogrammer on 2011-01-13
Try with

sudo apt-get check

sudo apt-get update


sudo apt-get upgrade


sudo apt-get autoremove


sudo apt-get autoclean

sudo touch /forcefsck

then restart

---

### Post by deauvilleuk on 2011-01-13
But the keyboard doesn't work ?

---

### Post by Mark Phelps on 2011-01-13
Try plugging in a USB keyboard.  IF it detects that, you can enter the commands.

But if those don't fix it, you're pretty much hosed regarding Ubuntu use on the laptop.

---

