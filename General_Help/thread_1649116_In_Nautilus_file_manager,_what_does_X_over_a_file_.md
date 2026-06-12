---
title: "In Nautilus file manager, what does X over a file or folder mean?"
date: 2010-12-19
forum: General Help
---

### Post by tc101 on 2010-12-19
In Nautilus file manager, what does X over a file or folder mean?

---

### Post by PhantmKllr on 2010-12-19
It usually means "Unreadable".

---

### Post by drewsus on 2010-12-19
While not entirely incorrect, it is, more accurately, that you are neither the owner nor in the group that has permissions to read/write/execute to that particular folder/file.

---

### Post by tc101 on 2010-12-19
I am confused.  I used Simple Backup to backup my system, and the files it created have that X.  I am able to restore data from them but I am not able to copy them to another location.

---

### Post by drewsus on 2010-12-19
You can restore your data using Simple Backup but cannot move them via nautilus?
So, exactly what I said previously. Do you have to enter your password when using Simple Backup.
Screen shots and a more verbose description may help. 
Furthermore, navigate to the folder that has said files/folders and run this command and post the output (in code tags):
```
ls -l
```

---

### Post by tc101 on 2010-12-19
Thanks.  I understand now.

---

