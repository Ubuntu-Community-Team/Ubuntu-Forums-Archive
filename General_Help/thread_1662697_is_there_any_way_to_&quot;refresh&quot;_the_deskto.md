---
title: "is there any way to &quot;refresh&quot; the desktop"
date: 2011-01-08
forum: General Help
---

### Post by JuicyCouture on 2011-01-08
sometimes i'll log in and the icons for the applets at the top (my username, the volume icone etc.) will be messed up like blurred vision almost, like two of them smeared together

if something ugly like this happened on windows i remember i would usually just right click and refresh and it would (sometimes) fix the problem

anything like this on ubuntu?

---

### Post by Verbeck on 2011-01-08
you mean the icons on the desktop seem to be on top of each other?
then, right click > 'organize desktop by name'

edit: re-read your post. 
try from a terminal, *pkill gnome-panel*

---

### Post by mc4man on 2011-01-08
Most effective way when the panel applets are messed up is ether do a quick log out/in or you can r. click on the applet(s) - remove from panel and then r. click and add them back.

The log out/in is easier and quicker.
If you wish open Preferences -> Keyboard -> Layouts -> Options and re-enable Ctrl+Alt+Backspace to restart (kill) X server

---

