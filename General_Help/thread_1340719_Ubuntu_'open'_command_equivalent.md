---
title: "Ubuntu 'open' command equivalent?"
date: 2009-11-28
forum: General Help
---

### Post by growthmetal on 2009-11-28
On Mac OS X there is an exceedingly nifty terminal command 'open' which will do whatever the default action associated with double-clicking its argument is.  Is there an equivalent command on Ubuntu?  If not, any clues on writing one?

---

### Post by audiomick on 2009-11-28
Hallo.
I have no idea if such a command exists, but tried something just to see.

type
```
man open
```

in a terminal.

I think that might be what you want.

---

### Post by amingv on 2009-11-28
You're looking for 'xdg-open'.

(You can alias it to "open" if it's more natural to you.)

---

### Post by sisco311 on 2009-11-28
Ubuntu (GNOME):
```
gnome-open
```

Xubuntu (Xfce):
```
exo-open
```

Kubuntu (KDE):
```
kde-open
```

---

