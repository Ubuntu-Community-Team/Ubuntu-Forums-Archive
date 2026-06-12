---
title: "How do I move a folder into a different location"
date: 2011-11-05
forum: General Help
---

### Post by alexandros81 on 2011-11-05
Hi. I want to move a folder or a file to /usr/lib location but when I drag and drop the file or folder the message in the picture attached appears.
As I have understood I don't have permission to do that. How can I get permission?

Is there a command in the Terminal window to copy a folder into a different location?

Alexandros

---

### Post by garyed on 2011-11-05
You should be able to use "mv" with "sudo"

```
sudo mv [folder] [folder-to-move-to]  
```

If you want to copy the folder instead of moving it then:

```
sudo cp -r [folder] [folder-to-move-to]  
```

---

### Post by alexandros81 on 2011-11-05
Thanks I have solved my problem. How do I change the status of this thread to *solved*?

---

### Post by haqking on 2011-11-05
> **alexandros81 said:**
> Thanks I have solved my problem. How do I change the status of this thread to *solved*?

use the thread tools menu, also good to read  [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") for future reference.

Cheers

---

### Post by mick222 on 2011-11-05
You could also use gksu nautilus if you want drag and drop.Just press alt f2 then type it in the box.

---

