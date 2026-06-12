---
title: "lost+found?"
date: 2011-07-03
forum: General Help
---

### Post by samuel.cole on 2011-07-03
i can't delete a file called lost+found in an encrypted file i made because i dont have permissions to read it even though im the root?

](*,)

---

### Post by eric3_14159 on 2011-07-24
What permissions does it have? Root has to obey file permissions, it just has the ability to alter them. In general, you need to give root write permission to be able to delete it. If root is the owner, then "chmod u+w lost+found" should be enough. If not, you can just run "chmod a+w lost+found" and then delete it.

---

### Post by Miljet on 2011-07-25
Lost+found should be a directory, not a file. It is where orphaned file fragments are placed during a disk check. Even if you manage to delete it, it will be re-created the next time fsck runs.

---

### Post by wildmanne39 on 2011-07-25
Hi, that is exactly right it will recreate it, so it is best left alone.

---

