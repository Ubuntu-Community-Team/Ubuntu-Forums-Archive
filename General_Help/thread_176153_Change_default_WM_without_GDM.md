---
title: "Change default WM without GDM"
date: 2006-05-14
forum: General Help
---

### Post by TFleck on 2006-05-14
I dont wanted to boot with GDM, so I turned it off. But I use fluxbox as my default WM, and when I start the X server from the textmode (with startx command) it loads GNOME.
How can I make it load fluxbox instead?

---

### Post by richbarna on 2006-05-14
If you use the GUI start up login, there is a tab that says "session", click it and choose what window manager you like.

---

### Post by TFleck on 2006-05-14
That's the way I was using to change to Fluxbox.
I'm tring to find a way to use it as default when loading X from the textmode.
And I found it:
create a file ~/.xinitrc with 'exec fluxbox' in it.

Is there a better way for doing it?

---

