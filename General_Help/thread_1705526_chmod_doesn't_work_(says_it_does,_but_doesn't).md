---
title: "chmod doesn't work (says it does, but doesn't)"
date: 2011-03-12
forum: General Help
---

### Post by nc_jed on 2011-03-12
What gives?

```

blake@servey486:/media/usb$ sudo chmod -v 777 *
mode of `Chandler' changed to 0777 (rwxrwxrwx)
mode of `Gardner' changed to 0777 (rwxrwxrwx)
blake@servey486:/media/usb$ ls -al
total 100
drwxr-xr-x  4 root root 32768 2011-03-12 09:26 .
drwxr-xr-x 12 root root  4096 2011-02-04 18:02 ..
drwxr-xr-x  2 root root 32768 2011-03-12 09:26 Chandler
drwxr-xr-x  2 root root 32768 2011-03-12 09:26 Gardner
blake@servey486:/media/usb$ 

```

If it makes a difference, this is a vfat USB drive on a headless ubuntu server (10.10).

-NC_jed

---

### Post by vanadium on 2011-03-12
You know that the vfat file system does not support Linux permissions? Like you, I would indeed expect an error message, though.

---

### Post by jerome1232 on 2011-03-12
File permissions for MS filesystems are set for the entire drive at mount time, there is some good info about in in this post somewhere [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

edit: I remember something about chmod can be configured to either give errors or not when attempting on ms filesystems.... I'm on a windows machine atm so can't check.

---

### Post by nc_jed on 2011-03-12
> **jerome1232 said:**
> File permissions for MS filesystems are set for the entire drive at mount time, there is some good info about in in this post somewhere [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

edit: I remember something about chmod can be configured to either give errors or not when attempting on ms filesystems.... I'm on a windows machine atm so can't check.



Thanks for the feedback, both of you.  In the process of trying to figure out this issue, I lost sight in the fact that I'm setting this up as a network SAMBA share for a couple of Windows clients, so I suppose it's a moot point.  For my Linux accesses, I can just Sudo it.  Thanks for the feedback, though!

- Jed

---

