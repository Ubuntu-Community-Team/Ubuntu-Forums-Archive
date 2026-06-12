---
title: "Disable Ubuntu 10.10 GUI"
date: 2010-10-28
forum: General Help
---

### Post by adam35413 on 2010-10-28
I recently installed Ubuntu 10.10 on a system that has turned into a server.  I have attempted to disable GNOME from loading using various methods I have found through Google such as ```
sudo update-rc.d -f gdm remove
``` but on restart GNOME just starts up again.  I also ran ```
sudo aptitude remove ubuntu-desktop
```.  Again, on reboot GNOME still started.

What is the method to disable the desktop on Ubuntu 10.10?

---

### Post by sisco311 on 2010-10-28
Edit /etc/default/grub and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"**, then generate a new grub2 config file:
```
sudo update-grub
```

---

### Post by adam35413 on 2010-10-28
That did it.  Thanks a lot!

---

