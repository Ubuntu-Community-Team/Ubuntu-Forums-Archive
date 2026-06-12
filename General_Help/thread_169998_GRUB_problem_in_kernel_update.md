---
title: "GRUB problem in kernel update"
date: 2006-05-03
forum: General Help
---

### Post by eliabramo on 2006-05-03
hi
I have dual boot with grub for my winxp and dapper.
every time I upgrade the kernel, the debian installer comment the lines of the winxp, and I need to uncomment them manually.

why it's happens? can I fix it?

---

### Post by GTvulse on 2006-05-03
Yes, read the comments in /boot/grub/menu.lst.

You have surely placed the WinXP lines within the block marked as "AUTOMATIC KERNELS LIST". As it says clearly there, it is managed by the installation scripts. Anything you write there, will be gone after updating the kernel.

---

