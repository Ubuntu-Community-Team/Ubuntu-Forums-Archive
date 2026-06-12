---
title: "set evince to maximize window by default"
date: 2012-03-11
forum: General Help
---

### Post by MichaelBurns on 2012-03-11
I run Lucid Live on a netbook.  Is there a way to set Evince (pdf viewer) to always launch to maximized window by default?  I tried to find a gconf setting, and looked around in the hidden folders and files in my home directory, but no luck.

---

### Post by kalos on 2012-11-28
You could try installing [maximus]("apt://maximus"). It will maximize windows when they're launched.

Just install it and then run ```
maximus
``` from a terminal. If you like it, then open Startup Applications and add Maximus with Command: /usr/bin/maximus

I find it's not working great for me (windows are maximized, but they are partially above the top of my screen) in 12.04 with Unity, but maybe you'll have better luck.


Alternatively, you could try to figure out [Compiz's Place plugin]("http://wiki.compiz.org/Plugins/Place"). I think it would let you just modify evince. (But I have no idea how it works.)

---

### Post by Tinker Tantrum on 2012-11-29
Have you tried his suggestions yet? Have they worked? Because I am having the same issue.

---

