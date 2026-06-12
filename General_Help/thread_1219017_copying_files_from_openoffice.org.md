---
title: "copying files from openoffice.org"
date: 2009-07-21
forum: General Help
---

### Post by Len Tyree on 2009-07-21
i am attempting to copy files from openoffice.org onto a floppy, but am unable to do so,  the copy command does not recognize the openoffice,org file.

so, i guess i need 'explicit' instructions on how to copy these files, or   need someone to hold my hand while i push buttons.

any help would be appreciated.
thanks, len tyree.

---

### Post by jerrrys on 2009-07-22
i don't have a spare floppy laying around to make sure of this, but it should be a simple drag from home folder and drop to floppy operation.  copy not necessary.

---

### Post by Tyke91 on 2009-07-22
are you trying to copy a document?

if it is, do you know where you saved it?

do you know where the floppy is mounted?

if all of these answers are YES, then we are in business :)

i'm going to assume your document's name is "foo.odt" and that you saved it to /home/yourusername/Documents and that your floppy is in /media/floppy

```
cp -v ~/Documents/foo.odt /media/floppy
```

---

