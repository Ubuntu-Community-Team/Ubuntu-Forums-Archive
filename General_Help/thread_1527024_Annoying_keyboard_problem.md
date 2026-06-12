---
title: "Annoying keyboard problem"
date: 2010-07-08
forum: General Help
---

### Post by Lijnk on 2010-07-08
Almost every time when I'm typing, I come across this weird thing where something random happens. It can range from the object in the clipboard suddenly pastes itself, a random thing from the page I'm on, or from another tab places itself in the textbox like I pasted it and can even go as far as to close tabs, or windows. I'm using Ubuntu 10.04 on an eee pc 1001p.

---

### Post by tgalati4 on 2010-07-08
Are you taking your medicine?

Open a terminal and run xev.  Put the mouse in the xev window and slowly press each key.  You should see press and release events for each key.

Try an external USB keyboard and see if you get the same behavior.

Page through dmesg and look for keyboard errors:

dmesg | more     (spacebar to move forward, q to quit)

---

