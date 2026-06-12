---
title: "How To Make A  Password Protected Folder ?"
date: 2011-05-22
forum: General Help
---

### Post by N0LA on 2011-05-22
Hello , Im a Total begginer when it comes to Ubuntu , and i was wondering if i can make a hidden folder or a password locked folder / How To If So ? 

Keep In mind Im a Total begginer with Ubuntu

---

### Post by hawthornso23 on 2011-05-22
Cryptkeeper might be what you are looking for. It is for managing and mounting encrypted folders.

---

### Post by coldraven on 2011-05-22
Any folder or file name that starts with a "." (a dot) will be hidden.
In Nautilus the file browser press Ctrl+h to toggle showing hidden files.
Try it yourself, open Applications>Accessories>Text editor, write something and save it as .test.txt

---

### Post by Wim Sturkenboom on 2011-05-22
And change the permissions to 700 (owner can read,write and descend into the directory, nobody else can).

It however depends on the reason why you want this. If you want to prevent other computer users fromn seeinhg it straight away, hidden files/folders and permissions are probably the easiest. However, if somebody comes with e.g. a live CD, he/she can still find it and access it. To prevent that, you indeed need an encryption.

---

