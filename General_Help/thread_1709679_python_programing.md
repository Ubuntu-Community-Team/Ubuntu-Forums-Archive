---
title: "python programing"
date: 2011-03-18
forum: General Help
---

### Post by Unguidedone on 2011-03-18
[http://stackoverflow.com/questions/1181464/controlling-mouse-with-python](http://stackoverflow.com/questions/1181464/controlling-mouse-with-python)

how can i do the same thing on linux?  where are the guides for all the built in commands?

---

### Post by lykwydchykyn on 2011-03-18
Like most Linux distros, Ubuntu uses X (a.k.a. X11, Xorg, X server, etc) for its display.  The mouse is controlled by X.  So, for doing this kind of thing in python, you need to use python-xlib.

 - Install python-xlib from the repositories
 - Open a python shell and try this:
```

from Xlib import display
d = display.Display(":0")
d.warp_pointer(400,400)
d.flush()

```

That sample code should move your mouse cursor 400 pixels down and 400 pixels right.

Complete documentation on xlib is here: [http://python-xlib.sourceforge.net/doc/html/index.html](http://python-xlib.sourceforge.net/doc/html/index.html)

---

### Post by GregBrannon on 2011-03-18
The Programming Talk sub-forum here on UF is a good place to ask these kind of questions and to learn more by reading stickies and reviewing/searching existing threads.

---

