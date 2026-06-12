---
title: "Cannot make the file executable"
date: 2011-03-22
forum: General Help
---

### Post by r_anjit on 2011-03-22
It so happens that some files that I am trying to make executable by chmod +x <filename> or otherwise are not becoming executables, rather  the tick mark on the option is removed the very instant I put it on . Is there any thread of virus or any other reason for this..


Thanks!! as always.

---

### Post by TeoBigusGeekus on 2011-03-22
Can you give us an example? If possible attach the file.

(Forget about the virus by the way).

---

### Post by nothingspecial on 2011-03-22
fat or ntfs drives will not let you chmod +x a file.

---

### Post by TeoBigusGeekus on 2011-03-22
> **nothingspecial said:**
> fat or ntfs drives will not let you chmod +x a file.

Yes, of course...
+1

---

### Post by vivek.pandey on 2011-03-22
hi
you can try this... i guess the file you are trying to mark as executable is not in your ubuntu partition but perhaps in windows or any other os... what i mean is  you have most likely dual boot . to make that particular file executable bring it in ubuntu partition ie your home directory in ubuntu and try again

---

### Post by 3rdalbum on 2011-03-22
You can't have execute permission on filesystems that don't support it (such as NTFS) and you can't set it on read-only media (such as CD-ROMs).

You don't need execute permission on programs to run them in Wine - just open a terminal and type 'wine ' and then drag the program to the terminal. Foreground the terminal and press Enter to run the command.

---

