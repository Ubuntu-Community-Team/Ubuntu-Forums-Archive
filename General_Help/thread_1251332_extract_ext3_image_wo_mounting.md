---
title: "extract ext3 image w/o mounting?"
date: 2009-08-27
forum: General Help
---

### Post by picopir8 on 2009-08-27
Does anyone know of a way to extract the contents of an ext3 image file w/o loopback mounting it?  Ideally I would like something that does the reverse fo e2fsimage.  That is, it would create a directory and extract all files to that directory and change the user/group id to that of the user who extracts the file.

BTW, I would like to put this in a script that other users could run and those users can not be allowed have access to mount/unmount.

---

### Post by picopir8 on 2009-08-28
bump...

---

### Post by pastalavista on 2009-08-28
If, by "ext3 image file" you mean a .img archive I believe you or any user can open it with file-roller Archive Manager in the Applications > Accessories menu and extract files or whatever.

---

### Post by picopir8 on 2009-09-08
The only file system image that file-roller can read is iso.  It will not read ext3 images.

[http://fileroller.sourceforge.net/features.html](http://fileroller.sourceforge.net/features.html)

This should not be this difficult.  I find is silly that just about every linux box will automount a disk or USB drive, but if a user wants to mount a file system image that they own or have permission to access, then they still cant do a darn thing unless they are root.

Mount should really be permission based and then sudo/root access should only be required if the device/file owner is anyone except the user running the command.  Hopefully this will change in the future.  Until then, if anyone has a work around I would be happy to hear it.

---

