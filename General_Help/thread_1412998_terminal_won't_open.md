---
title: "terminal won't open"
date: 2010-02-21
forum: General Help
---

### Post by iu34 on 2010-02-21
okay, I hope I'm not screwed...

I was using vim in gnome-terminal, it was working fine. I save my document, close out of the terminal. A few minutes later, I go back into the terminal. Only this time, it flashes on the screen and disappears.

So, I decided "Well, I'll just look it up later." and proceed to use Guake for the same purpose -- editing using vim. Now, guake won't open either.

Ubuntu 9.10

Help?

---

### Post by blazemore on 2010-02-22
Hit alt+f2 and type xterm then press enter.
If that brings up a terminal, try running gnome-terminal from there and see if it gives an error.

---

### Post by NCLI on 2010-02-22
Did you exit Vim before closing the terminal? Otherwise, you may have to go to Gnome System Monitor and kill vim and/or gnome-terminal.

---

