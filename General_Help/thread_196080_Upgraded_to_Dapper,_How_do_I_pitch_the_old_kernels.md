---
title: "Upgraded to Dapper, How do I pitch the old kernels?"
date: 2006-06-13
forum: General Help
---

### Post by Koori23 on 2006-06-13
Hi,

I've upgraded to Dapper from Breezy, how do I clean up the old Kernel's and/or clean up the grub menu so I don't have a page worth of options when I startup? 

If I can't get rid of the old kernels, how much space do they take up? Is it even worth the trouble?

---

### Post by Ctrl+Alt+Del on 2006-06-13
The Kernels are only a few megabytes each, no need to delete them.
In ordner to remove the unneeded options from the grub menu you can edit your  /boot/grub/menu.lst and remove the old entries.

---

### Post by bukwirm on 2006-06-13
Run 'sudo aptitude', find the packages labeled obselete, and remove them. This should get rid of all packages that are not being used.

---

