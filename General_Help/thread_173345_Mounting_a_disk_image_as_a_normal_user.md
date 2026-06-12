---
title: "Mounting a disk image as a normal user"
date: 2006-05-10
forum: General Help
---

### Post by bjourne on 2006-05-10
I want to be able to mount a disk image as a normal unprivileged user:

$ cd ~
$ mount -t ext2 -o loop bootfile.img floppy
mount: only root can do that

IMHO it is very stupid that mount tells me that only root can do that when I'm trying to mount a disk image file in my own home directory on a mount point also in my own home directory. I know about sudo but it shouldn't be required for this case and I'm trying to create a script to automate things so sudo is not an option.

---

### Post by DeadEyes on 2006-05-10
I think for a normal user to mount something there needs to be and entry
in the fstab file with a "user" option. or is a disk image a special case?

---

### Post by bjourne on 2006-05-10
That doesn't work for me. The image to mount and the mount point can be anywhere on the filesystem so it is not possible to specify it in fstab.

---

### Post by DeadEyes on 2006-05-15
try searching [http://www.misticriver.net/forums.php](http://www.misticriver.net/forums.php)

---

