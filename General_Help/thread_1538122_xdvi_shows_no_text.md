---
title: "xdvi shows no text"
date: 2010-07-24
forum: General Help
---

### Post by robobart on 2010-07-24
Hi,

Here is a very strange problem: When working on my laptop (Dell Latitude E4300, 10.04) xdvi shows no text when viewing a dvi file (evince works ok though).

However, when I doc my laptop and use an external monitor xdvi works fine!?

What is going on?

---

### Post by gordintoronto on 2010-07-24
Any chance it's printing white-on-white? [smile]

What version of xdvi are you using? There doesn't seem to be "xdvi" in the repositories.

---

### Post by robobart on 2010-07-24
I'm using Xdvik 22.84.16  

Another piece of the puzzle - if I "zoom" via the mouse buttons, I can see the text - it is black.

I don't think I accidentally changed the color of the background text. Is there an easy way to check?

(besides if I had changed the color, it would be that color upon zooming too, at least I think so)

Thanks!

---

### Post by flaviomoura on 2010-08-19
This happened to me. The text appeared again after maximizing the xdvi window... very strange :-)

---

### Post by cypeng on 2010-11-06
I confirm the same bug reported, this time using Thinkpad X200.  Strangely, using a really old Thinkpad X23, with the same xdvi installation of version 22.84.16, there does not appear to be a problem.

I also confirm that maximizing the window makes the problem go away.  In fact, it seems like xdvi "wakes-up" when one plays with the window size in any manner and the problem goes away.

This bug may be related to another bug with the expert mode.  It appears that the expert mode toggle is busted in the sense that the display appears empty in "xdvi -expertmode 0 ..." and 1, but is fine in expertmode 2 and 3, but then goes blank again in expert mode 4 and 5, then is ok again in 6 and 7, then blank again in 8 and 9, repeat.

In fact, toggling the expert mode also toggles the problem on and off, but only on the *next* start-up of xdvi, rather than the current session.  Related to this, there appears to be yet something else:  When one toggles the menu buttons off using the "x" key while xdvi is running, they cannot be toggled back on again.  Toggling the menu buttons off in one session actually makes the xdvi display go blank the next time it fires up.  Toggling the menu button once more (even though you cannot see it activated) makes things go back to normal again on the *next* restart of xdvi.

Hopefully someone reading this will know exactly what the problem is based on these clues.

---

### Post by plm.qwer on 2011-03-30
I am having a similar issue.

When xdvi is launched through
  xdvi filename.dvi,
everything seems normal.

However, when it is launched through
  xdvi -paper a4 -s 6 filename.dvi,
the window appear blank initially, and it will be "wake up" when it is maximized, or when its button at the task bar is pressed twice.

---

