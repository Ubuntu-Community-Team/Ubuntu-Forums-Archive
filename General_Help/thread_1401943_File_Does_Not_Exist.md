---
title: "File Does Not Exist"
date: 2010-02-08
forum: General Help
---

### Post by PropheticAngel on 2010-02-08
Ubuntu 9.10 - Karmic Koala
Laptop - Thinkpad T60
External Hard Drive - Iomega eGo

I have a file on my external that I can't delete.  I can see it in nautilus but it says it can not be sent to trash and must be permanently deleted.  After that it tells me it cannot delete it because there is no such file or directory.

I get the same error when I try to sudo rm the file.  I know the 'file' used to be a folder (it was a CD).  Now I can open the file and I see:

[Trash Info]
Path=path/to/file/I/deleted/not/this/one
DeletionDate=2010-02-03T18:40:15

How do I fix this?

---

### Post by Mr Nemo on 2010-02-08
Did you try to delete it through 'sudo nautilus'?

---

### Post by dearingj on 2010-02-08
Have you tried using "sudo rmdir" rather than "sudo rm"?

---

### Post by PropheticAngel on 2010-02-08
Tried sudo nautilus.  Same Thing.  Terminal displays

** (nautilus:3543): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files

when I start to delete it.  Don't see how that could be linked though.

---

### Post by PropheticAngel on 2010-02-08
> **dearingj said:**
> Have you tried using "sudo rmdir" rather than "sudo rm"?

Yes, it says it is not a directory.

---

