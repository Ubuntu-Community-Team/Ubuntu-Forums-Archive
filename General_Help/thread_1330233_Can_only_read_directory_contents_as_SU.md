---
title: "Can only read directory contents as SU"
date: 2009-11-18
forum: General Help
---

### Post by Captain Giraffe on 2009-11-18
I have a local filesystem directory where my normal user is owner of . , .. and all the other files. My normal user cannot however read the contents of the directory, only a "sudo ls" can read the contents. 
All the file attributes looks normal under sudo ls, but when I list the directory as a normal user I get all attributes listed as
d????????? ? ? ? ?                ? ../
-????????? ? ? ? ?                ? filename
Also all subdirectories (that the normal user owns) gives "ls: cannot access .... Permission denied"
Any ideas on what might be causing this?

---

### Post by Captain Giraffe on 2009-11-18
Shameless bumb

---

