---
title: "backing files"
date: 2011-12-02
forum: General Help
---

### Post by esky64 on 2011-12-02
ubuntu has now crashed (grub I think) well either MBR or partition table 
How can I backup my files 
tried live 10.10 but it can't copy all the files no permission on some PDF and ISO files

---

### Post by BC59 on 2011-12-02
Sometimes using Live CD and copying files from a computer, you have problems with permissions.

Try to use ```
gksudo nautilus
``` from a terminal to copy the files.

Then while you have the folder of files copied this way, on the new installation, running gksudo nautilus again, you can change the entire folder permissions, because we will have problems to open them.

---

