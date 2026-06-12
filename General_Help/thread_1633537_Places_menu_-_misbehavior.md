---
title: "Places menu - misbehavior"
date: 2010-11-29
forum: General Help
---

### Post by windfix on 2010-11-29
On a fairly fresh Maverick install, the folder shortcuts in my Places menu (Home Folder, Desktop, Documents,...Downloads) fail to work.  Instead, they attempt to launch OpenOffice, which does not actually load past the splash screen.

The remaining shortcuts under Places do work (Computer through Recent Documents).

Any clues or fixes appreciated!

---

### Post by windfix on 2010-11-29
OK, I found the solution.

In ~/.local/share/applications/mimeapps.list 

Mine had:

inode/directory=OpenOffice-Writer.desktop (or something like that)

Changed to:

inode/directory=nautilus.desktop

and Presto, back to normal.  I have no idea how this got changed in the first place.

---

