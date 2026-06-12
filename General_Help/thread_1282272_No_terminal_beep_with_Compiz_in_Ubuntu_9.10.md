---
title: "No terminal beep with Compiz in Ubuntu 9.10?"
date: 2009-10-04
forum: General Help
---

### Post by Hund on 2009-10-04
Hi,

I have Ubuntu 9.10 and when I'm not running Compiz the terminal beep works, but when I'm using Compiz it doesnt work at all.

I have no idéa how to fix this?

---

### Post by CatKiller on 2009-10-04
There's a setting in CompizConfig Settings Manager &#8594; General for *Audible Bell* (at least in Jaunty).

---

### Post by Hund on 2009-10-04
Thats already checked.

---

### Post by R@d0n on 2009-10-10
Hund:

In Terminal, go to Edit, Profiles. Select Default and hit Edit. Look for Terminal Bell, and uncheck it.

:popcorn:

EDIT:

Oops, I misread your post. That's how you disable it. X.X
Sorry about that.

---

### Post by Hund on 2009-10-10
This is really annoying since both LinuxDC++ and Xchat uses the same sound notification. :(

---

### Post by Hund on 2009-10-11
The correct name seems to be "Alert sound".

---

### Post by Hund on 2009-10-21
Found the problem.

[[img]http://pici.se/thumbs/t_zdgPrskUH.gif[/img]](http://pici.se/p/zdgPrskUH)

It was set to "0" in alsamixer.

---

### Post by raprap30 on 2009-10-21
I dont get it, you meant nulling the terminal? and the beep would sound?

---

### Post by mikeh on 2010-05-06
Still no beep in 10.04 lucid with Compiz. 
I can "modprobe pcspkr" so the system beep comes from the old-style PC speaker,
but would much prefer that compiz worked like metacity, and played a nice beep through the sound system.

---

