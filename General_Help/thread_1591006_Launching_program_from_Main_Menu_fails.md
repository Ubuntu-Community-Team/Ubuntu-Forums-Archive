---
title: "Launching program from Main Menu fails"
date: 2010-10-08
forum: General Help
---

### Post by Ranko Kohime on 2010-10-08
Well, this is an interesting problem.  I'm running GuitarPro6 on my EeePC, and it will only start correctly if I start it from a terminal, in the install directory (/opt/GuitarPro6)

If I attempt to start it from somewhere else, like ~/, I get a library error.  GP appears to want to look for this library in the working directory, and will only find it and start if I CD to /opt/GuitarPro6 first.

For this reason, I believe, when I click on the shortcut I made in Main Menu, nothing happens.

Is there any way to define the working directory for a shortcut in Main Menu?

---

### Post by sikander3786 on 2010-10-08
Did you look under System > Preferences > Main Menu. You can add, edit or delete any shortcuts from there. Update the command of GuitarPro6 to the one that you use in terminal. Might help...

---

### Post by Ranko Kohime on 2010-10-08
> **sikander3786 said:**
> Did you look under System > Preferences > Main Menu. You can add, edit or delete any shortcuts from there. Update the command of GuitarPro6 to the one that you use in terminal. Might help...
That is what I'm doing now...  For some reason, GP did not place an icon in the MM on install.  The problem is, I don't know how to force the working directory in the MM shortcut properties dialog.

---

