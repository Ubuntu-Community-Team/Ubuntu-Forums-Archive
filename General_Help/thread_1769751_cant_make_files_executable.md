---
title: "cant make files executable"
date: 2011-05-28
forum: General Help
---

### Post by debd on 2011-05-28
As the title says.. I cant make files executable anymore.
using chmod or from file properties.. it isn't working.
AS far as I remember, I didn't make any changes in the user settings and my account has the administrator rights. 
For an un-executable file, say a jpg or a txt, it can be done.
but doesn't happen with a .sh, .py or any other xecutable. chmodi-ing shows no error, but the file isn't executable. Through the GUI, when I  check the box , its immediately unchecked again. :(
I just cant get what's happening.

---

### Post by Petrolea on 2011-05-28
It doesn't work with 'sudo' and without 'sudo'?

---

### Post by WorMzy on 2011-05-28
NTFS and FAT partitions don't support Unix file permissions, so if the files you're trying to make executable are on one of these filesystems, either copy the file to a native filesystem (e.g. ext4), or use [this tutorial]("http://ubuntuforums.org/showthread.php?t=1604251") to set your NTFS/FAT partition to mount with specific ownership/permissions.

---

