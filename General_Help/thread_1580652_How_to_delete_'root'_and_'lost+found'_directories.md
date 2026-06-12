---
title: "How to delete 'root' and 'lost+found' directories"
date: 2010-09-23
forum: General Help
---

### Post by Lavix on 2010-09-23
Hi everybody!

I discovered two folders marked with a cross in my root:

- root
- lost+found

And when I'm trying to reinstall a newer version of Netbeans, 6.9.1. it claims that there is already something running in 'root folder

"The installer lock file exists at /root/.nbifile/.nbillock"

- The question is - is those folders are needed for Ubuntu working?
-If not how to delete them?

And one more question - how to delete a programme from the 'Applcations-Programming'?
I tried to do that via 'System-Preferencies-Main Menu' and tried to delete a previous version of Netbeans, but it didn't work, - nothing happens, the previous version is still there, so I have two ones - 6.9.1 and 6.9.

Thanks

---

### Post by srs5694 on 2010-09-23
The /root directory is the root user's home directory. Although Ubuntu does not (by default) permit direct logins as root, you should *not* try to delete that directory. A few files, like installer log files, get created there by default, and when you use certain administrative tools, it might be accessed for configuration files.

The /lost+found directory is a standard feature of the ext2/3/4 filesystems. If an fsck operation finds lost files, they'll become accessible in that directory. You should not attempt to delete it. If you're really offended by this directory, you could use another filesystem. IIRC, ReiserFS, XFS, and JFS do not create it. (I just checked, and ReiserFS definitely doesn't create it.)

As to removing programs from a menu, if you no longer need a program, you might try deleting its package using Synaptic. I can't promise this will work, but I'm pretty sure those lists are generated dynamically, so deleting the package should do the trick. (You might have to log out and then back in again to see the effect, though.)

---

### Post by Lavix on 2010-09-24
Thank you for the reply. As for root & C° folders it's clear for me now. As for deleting the netbeans 6.9 shortcut from the Programs menu, - the problem is that I had installed it via
```

sudo sh [netbeans-linux.sh] file

```
So I'm not sure that it will disappear (if it (at least the needed version) even exists in Synaptic package manager.
Anyway, I'll try, may it has already disappeared afetr the reboot, - I haven't booted yet:)

---

