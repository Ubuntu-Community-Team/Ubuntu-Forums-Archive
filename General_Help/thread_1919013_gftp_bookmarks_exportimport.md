---
title: "gftp bookmarks export/import"
date: 2012-02-02
forum: General Help
---

### Post by qjmann on 2012-02-02
Is it possible to export/import **gftp bookmarks** from one machine to another? Where gftp stores bookmarks?

---

### Post by deathadder on 2012-02-02
> **qjmann said:**
> Is it possible to export/import **gftp bookmarks** from one machine to another? Where gftp stores bookmarks?
There's nowhere in the GUI to export bookmarks, at least not that I've ever seen. But they are stored in a text file in: /home/USER/.gftp/bookmarks

You'll need to enable hidden files / folders in nautilus to see the gftp folder. You can then just send that file to the other machine and copy it back in place.

---

### Post by qjmann on 2012-02-02
> **deathadder said:**
> they are stored in a text file in: /home/USER/.gftp/bookmarks
Thank you, copying this file works!

---

