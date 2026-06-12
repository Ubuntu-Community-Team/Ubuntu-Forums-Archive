---
title: "Disabling close on a X11 window"
date: 2011-10-19
forum: General Help
---

### Post by nerdopolis on 2011-10-19
Hi.

I want to hide the close button and disable alt-f4 on closing a particular X11 window, and I don't think I can think of anything else. I tried fiddling about with xprop, wmctrl, and even using icewm, and setting a config file. Nothing seems to work or I might be doing something wrong...

I want to hide the Close button and prevent accidential closure of an Xephyr window, and eliminate confusion, as they should be using a different way to close it.

(This is for my Live CD project, not pc's that I am administering)

Any ideas?

---

### Post by nerdopolis on 2011-10-20
Any ideas?

---

### Post by nerdopolis on 2011-10-22
Bump?

---

### Post by merry_meerkat on 2011-10-25
I have no answer at all, but I would be interested in a solution, too.

I'd like to disable the close button on the skype window because it should minimise rather than close.

---

### Post by nerdopolis on 2011-10-26
I found a fix, I switched over the Window Manager for my Live CD to KWin, and I built the configuration file using the "Window Rules" KCM in systemsettings. From there, I you can set all sorts of policies on windows like if they have or don't have a close button, or if they can't be resized.

@merry_meerkat I guess it's going to depend on the window manager, other window managers can be configured like that but I think Kwin was the easiest, as it has a GUI to do so.

---

### Post by juzerali on 2012-09-01
Does a similar implementation exists for Compiz or metacity?

Otherwise can you give a little more details on how were you able to accomplish this with kwin?
Where is the exact file located which you edited and what did you change?

---

