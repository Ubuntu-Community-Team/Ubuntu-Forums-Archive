---
title: "Click to Mount"
date: 2010-08-26
forum: General Help
---

### Post by pulseplanet on 2010-08-26
Hello All

   I have a Network file system that I would like to mount on demand. Is there a way (as a user, not as sudo) to make an icon om my desktop that I can click to mount and unmount. I would like the icon to be persistent - ie it should not go away when I unmount the share.

Thanks
K.

---

### Post by thegod_slayer on 2010-08-26
well you can add the application disk mounter to your taskbar....
from there you can click to mount

---

### Post by pastalavista on 2010-08-26
you can also right-click the desktop and "create launcher" to run a terminal application (mount). there also has to be a 'user' tag in /etc/fstab for that drive if you don't want use sudo to mount it.

---

