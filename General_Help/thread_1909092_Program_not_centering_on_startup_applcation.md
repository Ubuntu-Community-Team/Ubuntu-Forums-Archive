---
title: "Program not centering on startup applcation"
date: 2012-01-14
forum: General Help
---

### Post by triunenature on 2012-01-14
So, I have a program that when it starts, should start in the center of the screen, for the python programmers:

```

center = gtk.WIN_POS_CENTER
window.set_position(center)

```

Ironically, the code works as advertised.  Here is the rub, when I start the program as a "Startup Application", it always starts at the very top left corner of the screen.

My theory is that maybe GTK hasn't been initailzed yet, and thus the gtk.WIN_POS_CENTER won't work, but the problem is I don't know how to fix it.  This isn't a python problem, because frankly the code works.  Its a Ubuntu/Linux issue.

Anyone know why this is happening, and how to fix it?

---

### Post by triunenature on 2012-01-15
I tried using time.sleep(20) to maybe give ubuntu more time to load, without success...

(this is more of a bump that additional information)

---

