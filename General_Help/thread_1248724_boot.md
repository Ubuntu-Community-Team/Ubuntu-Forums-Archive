---
title: "/boot"
date: 2009-08-24
forum: General Help
---

### Post by serpantman on 2009-08-24
If i copy the contents of /boot, then install windows on a second hd. Can i just copy these files back to /boot and have grub back to how it was before? Then just manually add boot instructions for windows?

---

### Post by serpantman on 2009-08-24
Is that how /boot works?

---

### Post by gastly on 2009-08-24
Nope, that will lead to a lot of problems. And, it's not a matter of simply copy-pasting the files, you will need Grub to install in the MBR.

If you're trying to install Windows with Ubuntu already installed, then follow this guide [here](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm).

---

