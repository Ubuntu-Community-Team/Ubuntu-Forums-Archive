---
title: "remember closed position"
date: 2010-06-01
forum: General Help
---

### Post by Chriis on 2010-06-01
Is there a way to linux to remember the position that a program was when closing them?

I hate to have to drag from upper left position at each time I open them.


But, maybe it's the only complaint i have about Lucid. 

Good Work! :)

Chriis

---

### Post by sedawk on 2010-06-01
Once upon a time people used the X11 file
.Xdefaults in the home directory to alter
default parameters to settings they liked.
E.g. changing the background and foreground colors
of an xterm.
```

xterm*background: grey30
xterm*foreground: black

```
You can also set a given width and height
or alter the offset on the screen.
The offset is changed with
```

xterm*geometry: +50+50 

```

As all modern desktops are still based on X11 that
might still work.

---

