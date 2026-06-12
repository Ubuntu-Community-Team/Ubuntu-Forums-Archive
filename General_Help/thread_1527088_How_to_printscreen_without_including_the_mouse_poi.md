---
title: "How to printscreen without including the mouse pointer?"
date: 2010-07-08
forum: General Help
---

### Post by xycris on 2010-07-08
Hi all,

I hope you can help me with my noob problem.

I was trying to do a research about capturing the screen in Ubuntu Lucid where we can exclude the mouse pointer but to my dismay there are no help I can find. Is my problem even solvable?

Thank you very much. I highly appreciate all the help and suggestions.

-Xycris

---

### Post by Johnny B on 2010-07-08
main menu > accessories > take screenshot
untick "include mouse pointer"

---

### Post by tgalati4 on 2010-07-08
In Jaunty, I just move the mouse to the edge of the screen and hit PrtSc (Printscreen button).  It takes a snapshot of the entire desktop (whatever is on the screen) and the mouse is not in the picture.  If you hit Alt-PrtSc then only the active window gets captured.  If the mouse is not in the active window, then it won't show up.

---

### Post by xycris on 2010-07-09
> **Johnny B said:**
> main menu > accessories > take screenshot
untick "include mouse pointer"

sorry Johnny B but it seems that feature is removed on Ubuntu UNR 10.04

@tgalati4: i am trying to take a series of shots that requires a mouse intervention to go to the next page.

is there something like untick the "include mouse pointer" when hitting the prntscn button?

---

### Post by tgalati4 on 2010-07-09
Have you tried scrot?

man scrot

If not installed:

sudo apt-get install scrot

---

### Post by jmszr on 2010-07-09
xycris,

Have you tried "Shutter"  If not: [https://launchpad.net/~shutter/+archive/ppa](https://launchpad.net/~shutter/+archive/ppa) .
It has a checkbox to exclude the cursor and is a very good screenshot app.

---

### Post by xycris on 2012-08-07
> **jmszr said:**
> xycris,

Have you tried "Shutter"  If not: [https://launchpad.net/~shutter/+archive/ppa](https://launchpad.net/~shutter/+archive/ppa) .
It has a checkbox to exclude the cursor and is a very good screenshot app.

hi jmszr,
i know this has been a long period sleeping but this tool solved my problem. thanks a lot. it is even included in the ubuntu software center!
thanks again. :)

---

