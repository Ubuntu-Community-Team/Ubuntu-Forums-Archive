---
title: "Grub trouble with Ubuntu 8.10"
date: 2011-03-10
forum: General Help
---

### Post by jehiva on 2011-03-10
Hello all,

I installed Ubuntu 8.10 on a separate partition after having installed Ubuntu 10.10 previously.  Following this, the Ubuntu 8.10 grub removed my old grub menu and this new Ubuntu 8.10 only shows Ubuntu 8.10 and Windows as boot options.

How can I either access Ubuntu 10.10 again, or change the mbr to use my original grub once again?

---

### Post by lithopsian on 2011-03-10
Do you have the 10.10 Live CD?  You can reinstall grub (which will be grub2) from there and it will be the new version again which should recognise both versions of Ubuntu.

Or you might be able to fix it very simply just by running update-grub (with sudo).

---

