---
title: "Editing multiple files"
date: 2010-06-28
forum: General Help
---

### Post by gio.fon on 2010-06-28
Hi.
I have a directory with hundreds of html files.
For all the files I have to:
- delete all the row from the beginning of the file to the sentence "<img src="immagini/_navDxBottom.gif" />".

- delete all the rows from the sentence "<br clear="right" />" to the end of the file.

How can I do that?
Thank you very much.
Giovanni.

---

### Post by Pollox on 2010-06-28
Regexxer might be useful for this ([http://regexxer.sourceforge.net/](http://regexxer.sourceforge.net/) ), and it is installable from the Ubuntu repositories.  It can replace text across multiple files using regular expressions.  This would still leave you to figure out how to write these expressions, unless someone else can help with this or has a better idea.

---

