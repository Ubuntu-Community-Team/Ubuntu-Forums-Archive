---
title: "I messed up install, and want to upgrade how can I if I can't boot?"
date: 2011-05-23
forum: General Help
---

### Post by CptanPanic on 2011-05-23
I messed up my install with an errant chmod *, so I have read that the best way to fix is to reinstall, I don't want to lose my configurations, so is there I way I can boot from install cd, and upgrade and not just reinstall which would make me lose all my config files?
Thanks,
CP

---

### Post by TeoBigusGeekus on 2011-05-23
If you mean your home folder, boot up with a live cd, back it up on an external drive/different partition, reinstall and then copy its contents in your new home folder.

---

### Post by CptanPanic on 2011-05-23
More than just home folder, like apache, samba, cron, and a bunch of other stuff I will forget.

---

### Post by ajgreeny on 2011-05-23
It sounds as if you also need to backup **/etc**, which contains a lot of configuration files and folders.  However, what did you do with the chmod command that has messed things up?  It may be possible to put it right.

---

### Post by CptanPanic on 2011-05-23
> **ajgreeny said:**
> It sounds as if you also need to backup **/etc**, which contains a lot of configuration files and folders.  However, what did you do with the chmod command that has messed things up?  It may be possible to put it right.

chmod 666 * -R for most of the drive.

---

### Post by ajgreeny on 2011-05-23
> **CptanPanic said:**
> chmod 666 * -R for most of the drive.
Oh dear, oh dear!!

Yes it will be a re-install certainly from that;  the problem with the filesystem folders that I suggested you might need in /etc is that they will also now have 666 permissions, if what you say you did worked.

Incidentally are you sure the permissions are now 666 for most of the filesystem?  The command you show is a bit back to front as the -R recursive option normally goes before the mode chosen of 666.  I have no idea if your way would cause an error message to appear or would work but it may be worth checking that the permissions are now 666, and show as **-rw-rw-rw-** or **drw-rw-rw-** when you use the ```
ls -la
``` command.

---

### Post by CptanPanic on 2011-05-23
> **ajgreeny said:**
> Oh dear, oh dear!!

Yes it will be a re-install certainly from that;  the problem with the filesystem folders that I suggested you might need in /etc is that they will also now have 666 permissions, if what you say you did worked.

Incidentally are you sure the permissions are now 666 for most of the filesystem?  The command you show is a bit back to front as the -R recursive option normally goes before the mode chosen of 666.  I have no idea if your way would cause an error message to appear or would work but it may be worth checking that the permissions are now 666, and show as **-rw-rw-rw-** or **drw-rw-rw-** when you use the ```
ls -la
``` command.

Yep I am sure.

---

