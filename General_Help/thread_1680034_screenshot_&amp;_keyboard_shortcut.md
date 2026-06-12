---
title: "screenshot &amp; keyboard shortcut"
date: 2011-02-01
forum: General Help
---

### Post by mife on 2011-02-01
Hi all, can you please help me with the following:

I frequently need to take screenshots of a game (flash-based, running inside a browser), in particular it's statistics screen which is shown when I hold the TAB key. The problem is, when I take a screenshot, either by pressing PrintScreen key or by pressing a custom-defined shortcut, the game responds to this keypress and hides its statistics screen, so the screenshot doesn't contain the information I need.

I figured out how to overcome this using a custom application launcher icon; but this requires using the mouse which is rather inconvenient.

Could someone suggest a way to define a shortcut that wouldn't be processed by the active application? Or maybe there's some screenshot utility that does this out of the box? 

Thank you.

---

### Post by sisco311 on 2011-02-01
Hi and welcome to the forums!

You can delay the command with a few seconds:
```
gnome-screenshot --delay=3
```
or
```
gnome-screenshot --window --delay=3
```

---

### Post by mife on 2011-02-02
Thank you for your answer. 

I'll give this a try, but I'm not sure if this is convenient. I'll have to press the shortcut, then press TAB and hold it for a while. Yes, this works around my problem of statistics screen, but it's like a slow autofocus of a cheap photocamera - you can't take a screenshot immediately.

---

