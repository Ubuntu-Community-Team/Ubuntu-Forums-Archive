---
title: "gksudo mount"
date: 2011-02-01
forum: General Help
---

### Post by mooreted on 2011-02-01
Trying to mount a ramdisk on demand when I need one, however gksudo is griping that the command is wrong. So, what's wrong with this command?

gksudo mount -t tmpfs -o size=1024m tmpfs /mnt/ramdisk

---

### Post by bodhi.zazen on 2011-02-01
mount is not a graphical application, use sudo

---

### Post by mooreted on 2011-02-01
Huh. Thanks. Well, how do I mount a ramdisk from on OpenBox menu if I can't use gksudo?

Guess I could change the sudoers file.

---

### Post by mooreted on 2011-02-02
Ah ha! Found a way to do it without changing sudoers. I created a bash script "ramdisk.sh" and put the mount command in there then I just call that script with gksudo from my OpenBox menu and gksudo pops up a password entry dialog, accepts the password and runs the script.

---

