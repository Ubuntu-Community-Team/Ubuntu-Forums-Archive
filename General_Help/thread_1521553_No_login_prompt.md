---
title: "No login prompt"
date: 2010-06-30
forum: General Help
---

### Post by mk12 on 2010-06-30
I can boot up ubuntu but it's just showing the default background, the login prompt won't come up. What do I do? startx doesn't work in the terminal (ctrl-alt F1), it gives an error. I can log in as root (recovery mode) and startx works and the desktop comes up though. Help!

---

### Post by Reffner on 2010-07-01
Did you try a fsck yet? If you can access the command line try a "sudo touch /forcefsck" to invoke a file system check at next boot.

---

### Post by mk12 on 2010-07-01
Yes , I can access the command line. I will try that tomorrow and let you know what happens, thanks. I would rather not have to reinstall Ubuntu.

---

### Post by mk12 on 2010-07-01
Ok, I did the "sudo touch /forcefsck" command and rebooted. When it started up it checked for errors, got to 100% and then rebooted by itself. Then when it started up again it checked for errors again, got to 100% and then went to do the same as before, default background but still no login prompt window. What do I do now?

---

### Post by mk12 on 2010-07-02
Bump.

---

### Post by Iowan on 2010-07-02
You can see if System>Administration>Login Screen (after unlocking) is set for Gnome or xterm.

---

