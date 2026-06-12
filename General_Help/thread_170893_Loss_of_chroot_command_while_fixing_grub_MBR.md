---
title: "Loss of chroot command while fixing grub MBR"
date: 2006-05-05
forum: General Help
---

### Post by PhilOSparta on 2006-05-05
I have a messed up grub MBR and found the following steps in a howto under a Hoary thread.

Others have found great success with these steps, but my system complains at step 6 with 
```

chroot: cannot run command `/bin/bash': No such file or directory

```
Why would the chroot command not be available?  mkdir, fdisk and mount worked okay.  This is a real puzzle.

Here's the steps I followed to restore GRUB / my initial MBR:

1. Boot with live Ubuntu CD
2. Get a terminal -> Applications -> Accessories -> Terminal
3. Make a folder -> sudo mkdir /mnt/ubuntu
4. Check the Ubuntu partition -> sudo fdisk -l (Mine is /dev/hda1)
5. Mount the root partition of Ubuntu -> sudo mount -t ext3 /dev/hda1 /mnt/ubuntu (replace /dev/hda1 by your Ubuntu partition determined at the step 4)
6. Chroot the mounted partition -> sudo chroot /mnt/ubuntu
7. Restore Grub / the initial MBR -> sudo grub-install /dev/hda
8. Exit the shell
9. Reboot

Any ideas?

---

### Post by DoktorSeven on 2006-05-05
Sounds like chroot can't run /bin/bash under your chroot, not that chroot isn't available.

Does /mnt/ubuntu/bin/bash exist after mounting it?

---

### Post by PhilOSparta on 2006-05-05
[QUOTE=DoktorSeven]Sounds like chroot can't run /bin/bash under your chroot, not that chroot isn't available.

Does /mnt/ubuntu/bin/bash exist after mounting it?[/QUOTE]
Thanks.  That has provoked several thoughts.  I will have to test for this later.

I would think that the chroot should exist under the Ubuntu Live CD at the point where I am calling it.   Therefore the chroot should work.  Right?

Wouldn't the /mnt/ubuntu/bin/bash be called after the chroot command does its thing? i.e. transfering the root file system over to the /dev/hda1.

---

