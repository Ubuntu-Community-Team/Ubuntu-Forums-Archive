---
title: "Changing files/ folders Owenship or permission"
date: 2010-09-21
forum: General Help
---

### Post by amrishp on 2010-09-21
Hello,
I have a strange problem after downloading a movie file. I noticed that I don't have permission to delete or change anything on this folder and files within it. I am attaching a snapshot image of the folder. please someone help me to delete this from my computer. thanks in advance. 

Amrish

---

### Post by mcduck on 2010-09-21
Where is the file located? If it's on any drive formatted as NTFS or FAT that would explain the lack of permissions, as those file systems simply don't support ownerships & permissions as they are used on Linux/Unix systems.

If it's on some Linux filesystem then you can simply use "sudo chown -R username /path/to/your /directory" to change the ownership to your user.

edit: Or if you really just want to delete it, run "gksudo nautilus" to open the file manager as root and delete it that way.

---

### Post by amrishp on 2010-09-21
Hello,

Thanks for all your help. using "gksudo nautilus" helped me to delete the file. once again thanks a lot. How can I make this thread as SOLVED?

---

