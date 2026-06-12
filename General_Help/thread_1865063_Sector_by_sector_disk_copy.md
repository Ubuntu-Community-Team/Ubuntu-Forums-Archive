---
title: "Sector by sector disk copy"
date: 2011-10-19
forum: General Help
---

### Post by erbad on 2011-10-19
I have a small USB drive that I would like to transfer onto another USB drive.

Rather then a drag and drop copy, I would like to do a sector by sector copy and I was wondering if there is an Ubuntu utility that could accomplish this task?

Thank you

---

### Post by oldfred on 2011-10-19
You can use dd which also has the nickname Data Destroyer. As if you do even a minor typo you likely damage something. reversing a character or wrong drive letter copies it exactly as you told it even if you did not mean that. dd also copies zero data so empty space adds to the time of the copy.

man dd

There is also this:
Full image backup
GNU ddrescue (packaged as gddrescue, though once installed the command is "ddrescue") 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

And I found this older link:
from caljohnsmith
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)


You can also use tar, but I have not used it.
man tar
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

---

