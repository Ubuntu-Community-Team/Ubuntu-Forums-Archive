---
title: "Network files are old."
date: 2010-02-19
forum: General Help
---

### Post by sshaikh on 2010-02-19
Sometimes when I need to access files held on a SAMBA(windows) PC, I find that I get an older version of the file. So for example:

1) Make and save a change to the file on the windows PC.
2) running "more /path/to/share/file" in Ubuntu will show the file before the change was made.

I presume Ubuntu is somehow caching this and other files. Is there any way of disabling this cache? A "no access" error would be preferable to an out of date file.

---

### Post by Iowan on 2010-02-19
Dunno if this is the case with Ubuntu, but the router project I used (FREESCO) didn't always immediately write files to disk unless you ran the **sync** command. Common practice was to run it twice ...

---

### Post by sshaikh on 2010-02-19
Ubuntu is doing the *reading* though. All edits are done on the machine where the files reside. Will sync work for that too?

---

### Post by sshaikh on 2010-02-22
Sorry to bug but does anyone have any ideas about this? It's becoming quite irritating as I don't know what files I'll be reading on the Ubuntu side.

---

