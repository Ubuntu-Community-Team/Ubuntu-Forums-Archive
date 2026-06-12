---
title: "No permissions to search"
date: 2010-03-23
forum: General Help
---

### Post by Boludinux on 2010-03-23
Hi Im trying to use the places -> search tool and I get the following error:

> The search results may be invalid.  There were errors while performing thisHere is a screenshot since some of the text can't be selected in the error box.

[IMG]http://i41.tinypic.com/2wdpv0g.jpg[/IMG]

---

### Post by dcstar on 2010-03-23
> **Boludinux said:**
> Hi Im trying to use the places -> search tool and I get the following error:
........


As it says, you do not have read permissions on those files.

Users do not necessarily have permissions to read other user's files.

---

### Post by n0dix on 2010-03-23
Problems with permissions. Try doing the search with root privileges.

---

### Post by Boludinux on 2010-03-24
Thanks for your reply guys, they were actually my files, I fix them by doing

> chown -R ariel:ariel ~

as root :D

---

### Post by n0dix on 2010-03-24
Don't forget to mark the thread as Solved ;)

---

### Post by Boludinux on 2010-03-24
Oops I forgot :D

---

