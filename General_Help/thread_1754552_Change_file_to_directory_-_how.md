---
title: "Change file to directory - how?"
date: 2011-05-10
forum: General Help
---

### Post by happy_pig on 2011-05-10
I have a usb that got corrupted whilst attached to a Vista computer.
Now what was once a directory is now a file!
It now reads as -rwxr -xr -x instead of drwxr -xr -x how do I change this back to a directory?

---

### Post by sj1410 on 2011-05-10
what is the extension of the file. did it get zipped or tarred.

---

### Post by WorMzy on 2011-05-10
If the USB stick uses FAT or NTFS, run chkdsk on it from Windows. If it uses a Linux filesystem, run fsck on it from Linux.

If the check doesn't at least recover your missing files, try using testdisk to recover them.

---

