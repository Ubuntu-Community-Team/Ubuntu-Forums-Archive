---
title: "verify usb drive"
date: 2011-01-31
forum: General Help
---

### Post by qwertyjjj on 2011-01-31
I am getting some weird things happening on my usb drive.
For example, I will copy a perfectly working adobe file to it and when I plug it in on another computer, it says it is corrupted.
I copy a movie file to it but on the other computer it refuses to open. Some files open successfully.

I tried to reformat it with gparted but it just errors out with no useful error code:
An error occurred while applying the operations
See the details for more information.
The details do not have any more information.

Can I verify the disk somehow?

---

### Post by TeoBigusGeekus on 2011-01-31
If your flash drive is ntfs, you could run a check disk to it from windows.
If it's ext3 or ext4, try to fsck it.

---

