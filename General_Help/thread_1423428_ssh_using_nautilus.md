---
title: "ssh using nautilus"
date: 2010-03-06
forum: General Help
---

### Post by spiky001 on 2010-03-06
I manage to ssh in server ok but when it opens i,m in file system is this correct seems abit vunrable? I would of expected to go to specific folder i.e a shared folder, if this is how it is then so be it

---

### Post by solar george on 2010-03-06
You still are constrained by the same user permissions as if you were at the console i.e. only if you are accessing the server at root (which you should NOT be doing) can you edit or delete important sytem files or read the passwd file ect.
With ssh (/sftp) there is no concept of a shared folder as mentioned above you can see and edit all you normally would as the user you are logged in as.

---

### Post by nothingspecial on 2010-03-06
You are logged in as the user you logged in as, so you can see the file system as that user would see it. You can only write, delete, edit etc root (or other user owned files/directories) with the sudo password, as if you were sat at that pc.

Have a look at public and private ssh keys if you are worried.

**EDIT - Slow today - EDIT**

---

### Post by spiky001 on 2010-03-06
Yep your rite was logging as root doh glad I asked now

---

### Post by solar george on 2010-03-06
In that case you really should look into disabling root login on the server.

---

### Post by spiky001 on 2010-03-06
done it found my mistake

---

### Post by nothingspecial on 2010-03-06
> **solar george said:**
> In that case you really should look into disabling root login on the server.

+1 as they say round these parts

---

