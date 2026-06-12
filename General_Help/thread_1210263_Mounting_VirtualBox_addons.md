---
title: "Mounting VirtualBox addons"
date: 2009-07-11
forum: General Help
---

### Post by Delano on 2009-07-11
Hello.

I've installed Ubuntu 8.04 on VirtualBox 1.6.4. I wish to install the VirtualBox additions, which mounts a virtual .iso file. There is a virtualboxadditions.run file located within the virtual .iso's root directory, but when I try to run it, it tells me I need administrator priviledges to do so. How may I access the directory from a terminal window and run it?

---

### Post by nice_like_rice on 2009-07-11
Where is the mount point? You could try from a terminal "cd /media", then "ls", then cd again to the mounted iso if it is listed there. Then you must type "sudo ./virtualboxadditions.run".


Edit, thought of an easier way.
Type "sudo nautilus" to open a file browser as root, then navigate to the file and simply click on it.

---

### Post by Delano on 2009-07-11
Thanks, that helped!

---

