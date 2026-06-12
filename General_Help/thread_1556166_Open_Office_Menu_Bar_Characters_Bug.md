---
title: "Open Office Menu Bar Characters Bug"
date: 2010-08-19
forum: General Help
---

### Post by jjjlong on 2010-08-19
If you look at the menu, the police, rows / columns... It seems Ubuntu don't recognise the caracters... what's the problem ? And how can I correct it ?[IMG]http://img710.imageshack.us/img710/9711/openofficebug.png[/IMG]

---

### Post by tim.sargent on 2010-08-19
I have been having the exact same issue, I just installed OOo about a week ago and this problem was noticed immediately.  OOo appears to still work, it is just hard to navigate and find what you are looking for in the menu bars.  Any help would be greatly appreciated.

---

### Post by jjjlong on 2010-08-19
Exactly. Everything works just fine. It's just the characters that are not showing up in the menus ... And get get very messy when trying to do new things with OOo.

---

### Post by jjjlong on 2010-08-20
After testing multiple times, trying to do anything I could think off... 

I found out it was working when using OOo as root, but not as user...

sudo openoffice.org will work
openoffice.org (or using Application Menu ) won'T work...

It seems to work, but it'S not a fix.

---

### Post by lyall on 2010-08-20
it looks like your default font is wrong 
if you can not change the default font 
then try removing Open Office and then install it

does Open office Writer or Impress do the same thing?
if not try and change the default in them and see if in work then in Calc

you can also see what font (language) you have installed by using Synaptic Package Manager
It might how installed the wrong language for you


good luck and have fun learning

---

### Post by Johann-1.0 on 2011-02-10
I have the same issue since I installed Ubuntu 64

---

### Post by Hagar Delest on 2011-02-14
See here: [[Solved] All menues are in Greek letters](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=1891).
Or you can try to install the gtk package for OOo in Synaptic, I've seen that it works too IIRC.

---

