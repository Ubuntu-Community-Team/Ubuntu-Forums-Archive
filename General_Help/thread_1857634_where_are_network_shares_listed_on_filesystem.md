---
title: "where are network shares listed on filesystem"
date: 2011-10-10
forum: General Help
---

### Post by agrayray on 2011-10-10
This question is actually related to my post on how to search files graphically on network shares connected through smb:

[http://ubuntuforums.org/showthread.php?t=1857130](http://ubuntuforums.org/showthread.php?t=1857130)

but i figured this warranted a separate post:

where are network shares mounted to on the filesystem in ubuntu?  I figured they would be in the /media or /mnt directories but i dont see them nor anywhere else that I can find them.   Is there a way to navigate to them in nautilus?  Not using the smb:// option of course but instead using the file system structure /.../...

Thanks in advance!

---

### Post by capscrew on 2011-10-10
> **agrayray said:**
> This question is actually related to my post on how to search files graphically on network shares connected through smb:

[http://ubuntuforums.org/showthread.php?t=1857130](http://ubuntuforums.org/showthread.php?t=1857130)

but i figured this warranted a separate post:

where are network shares mounted to on the filesystem in ubuntu?  I figured they would be in the /media or /mnt directories but i dont see them nor anywhere else that I can find them.   Is there a way to navigate to them in nautilus?  Not using the smb:// option of course but instead using the file system structure /.../...

Thanks in advance!
The Nautilus mounted shares are in your home directory (~) at:  ~/.gvfs

Edit: that is:  /home/<your_login>/.gvfs

Edit2: You can navigate there using Nautilus after using ***Ctrl+h*** to show the hidden files.

---

### Post by agrayray on 2011-10-10
Thanks capscrew!  That worked perfectly!

---

