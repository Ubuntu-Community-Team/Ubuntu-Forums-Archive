---
title: "Many X11 Folders"
date: 2010-05-23
forum: General Help
---

### Post by Crumbs744 on 2010-05-23
They are all inside each other, i stopped looking at about 15 levels.

Is that normal doc???

Ubuntu Srv 9.10

---

### Post by Crumbs744 on 2010-05-23
/Filesystem/usr/bin/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/

---

### Post by Elfy on 2010-05-23
[http://ubuntuforums.org/showthread.php?t=344704](http://ubuntuforums.org/showthread.php?t=344704)

quotes

> /usr/bin/X11 is a symlink to /usr/bin, it is there for compatabilty sake. It is no longer used by the latest versions of xorg, but some older apps might try to write there.
The reason you see the redundancy is that when you change to the folder /usr/bin/X11 it is still pointing to itself. It's a little confusing, but not a bug or virus.

> 
Actually, none of the repeated X11 folders are empty: they all have repeat the very same files. Do you still think I should delete them?

> No, your not getting it, it's a short cut to the folder your looking at so when you click the short cut it brings you back to the same folder over and over.

---

### Post by Crumbs744 on 2010-05-23
Ah, thanks. I did do a search but apparently not well enough!

---

### Post by Elfy on 2010-05-23
:lol:

First result for /usr/bin/X11

---

