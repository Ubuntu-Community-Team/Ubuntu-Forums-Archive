---
title: "missing Close,minanize and maximize bottons"
date: 2010-04-24
forum: General Help
---

### Post by Markjo12 on 2010-04-24
hello  guys
as you can see in the screen shot provided i'm missing my close,minimize and maximize botton that normally suppose to be at the right hand conor of an application. this goes for all of the application and i dont know what i did for this to happen.

---

### Post by 3rdalbum on 2010-04-24
Your window manager haas crashed. You can create a launcher on your panel with the following as its command:

metacity --replace

Or

compiz --replace

Then click the launcher and the window manager will be back.

If you were following the HOWTO about turning on RGBA transparency, this is probably why Metacity crashed (you need to be running Compiz to get RGBA anyway)

---

### Post by Ryan Dwyer on 2010-04-24
Alternatively, just press Alt + F2 and type the command.

---

### Post by 3rdalbum on 2010-04-24
> **Ryan Dwyer said:**
> Alternatively, just press Alt + F2 and type the command.

Alt-F2 doesn't work without a window manager running, trust me on that ;-)

---

