---
title: "Netbook Remix X11 Folder"
date: 2011-10-19
forum: General Help
---

### Post by Diverted Income on 2011-10-19
Found a folder sucking up valuable SD space. In the USR directory I have a directory called X11 and inside it another X11 and so on. What causes this and what can I do about it? Thanks!

---

### Post by WorMzy on 2011-10-19
X11 is the application that takes care of the graphical side of things. That said, you shouldn't have a folder called X11 *directly* inside /usr/.

/usr/bin
/usr/include
/usr/lib
/usr/share

should all have subfolders called X11, although they shouldn't take up that much space at all. Maybe six or so megabytes.

---

### Post by Diverted Income on 2011-10-19
I was wrong it is in /usr/bin/x11/x11/x11/x11/x11/x11/x11 and so on. Not sure how far it goes. Each x11 directory has 1520 items though.

---

### Post by WorMzy on 2011-10-19
Yeah, the X11 folder in /bin is just a symlink to /bin, which contains the X11->/bin folder symlink, etc. Ignore it, it doesn't actually take up any space.

---

