---
title: "How to permanently delete folders &quot;Music, Videos, Documents,....&quot; (through Nautilus)"
date: 2011-09-29
forum: General Help
---

### Post by pstein on 2011-09-29
I want to get rid permanently of the folders
 
- Music
- Videos
- Documents
- ...
in my Home folder (and in "Places" menu)
 
How can I delete them? I found no "delete" context menu entry in Nautilus file browser
 
If the existence is absolutely required I want to point them all to my Home base folder and delete the sub-folders
 
Peter

---

### Post by MG&amp;TL on 2011-09-29
I see no reason why this should not work:

1. Open terminal
2. ```
rm -r Music
rm -r Documents
rm -r...
```
etc.

EDIT: it DOES work.

---

### Post by MG&amp;TL on 2011-09-29
Just make sure that you have backed up your folders somewhere first.

---

### Post by pstein on 2011-09-29
> **MG&TL said:**
> I see no reason why this should not work:
 
1. Open terminal
2. ```
rm -r Music
rm -r Documents
rm -r...
```
etc.
 
EDIT: it DOES work.
 
Ok, the deletion works. 
 
BUT there are still links under/inside menu "Places".
 
How do I get rid of them as well?

---

### Post by TiBaal89 on 2011-09-29
I can't recall if my memory is confusing other OS's, but isn't there a possibility that applications will recreate these folders if they're absent?  That could get annoying if you're hard set against them not existing.

---

### Post by sisco311 on 2011-09-29
Delete the directories, then run:
```
xdg-user-dirs-update
```
this will reassign the XDG user directories to your home directory.

You might have to log out and log back in.

The documentation I found is kinda vague, but... well, here it is:
[http://www.freedesktop.org/wiki/Software/xdg-user-dirs](http://www.freedesktop.org/wiki/Software/xdg-user-dirs)

The Arch wiki also mentions the XDG user dirs:
[https://wiki.archlinux.org/index.php/GNOME_Tips#XDG_User_Directories](https://wiki.archlinux.org/index.php/GNOME_Tips#XDG_User_Directories)


HTH

---

### Post by Habitual on 2011-09-29
make a copy of ~/.config/user-dirs.dirs first with 
```
cp ~/.config/user-dirs.dirs ~/.config/user-dirs.dirs.org
```
then edit ~/.config/user-dirs.dirs and remove or comment (#) the Directories you wish to 'remove' permanently, THEN run 
```
xdg-user-dirs-update
```
then you can physically remove those directories you do not wish to have.

NOTE: DO NOT touch XDG_DESKTOP "" entry.

---

