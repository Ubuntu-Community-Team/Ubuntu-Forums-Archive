---
title: "Find kernel partition"
date: 2009-06-30
forum: General Help
---

### Post by helander on 2009-06-30
Is it possible from within a running system find out the partition the kernel was booted from, i.e. from what partition did the boot-loader load the kernel image?

Or if you used an initrd during boot, from what partition was this image loaded?

/Lars

---

### Post by t4thfavor on 2009-06-30
that information is inside of /boot/grub/menu.lst as far as I know there is no other way to extract it. But I don't know very much.

---

