---
title: "Cant save changed .conf file."
date: 2012-05-14
forum: General Help
---

### Post by DanLang on 2012-05-14
I had a problem with ubuntu that could only be solved by adding one line in a .conf file and when i wanted to save it,i could not press the save button and when pressing exit and choosing to "save as" it says i dont have the permissions necessary to save the file. what can i do to be granted this permissions?

---

### Post by plucky on 2012-05-14
> **DanLang said:**
> I had a problem with ubuntu that could only be solved by adding one line in a .conf file and when i wanted to save it,i could not press the save button and when pressing exit and choosing to "save as" it says i dont have the permissions necessary to save the file. what can i do to be granted this permissions?

Is it a system file?

Try ```
gksudo gedit <name of file>
``` to edit the file.

Good Luck

---

