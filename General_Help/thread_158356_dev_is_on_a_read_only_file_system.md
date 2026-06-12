---
title: "/dev is on a read only file system"
date: 2006-04-11
forum: General Help
---

### Post by vavoem on 2006-04-11
Hello,

Whenever i try to 
Sudo chgrp groupname /dev/raw1394 i get an error message
saying the filesystem it is on is read only.

Running Kubuntu breezy

---

### Post by vavoem on 2006-04-11
In grub you can change this

press escape  to get into grub menu.
go to the kernel of choice with arrow keys

press e for edit
replace the setting ro to rw 
go to the end of the line press enter

press b to boot

and you know you're laughin :-D

---

