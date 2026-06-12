---
title: "Install Grub2 from Live Natty CD"
date: 2011-03-31
forum: General Help
---

### Post by MrRichard on 2011-03-31
I've checked out another tutorial, but this command didn't work:
```
sudo grub-install /dev/sdb
```It says:
[CODE] /usr/sbin/grub-probe: error: cannot stat `aufs'.[/CODE
I was just about to finish an install of Natty when the installer crashed. Now I can't access my old version of Ubuntu. How would I be able to reinstall Grub2 back onto that partition?

---

### Post by wilee-nilee on 2011-03-31
That command would be run from inside the OS not a live cd, follow this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Look closely at the directions sdb is the hard drive=the mbr sdbX X=a number; that is a partition.

---

### Post by MrRichard on 2011-03-31
Thank-you! I better bookmark this page for future reference :)

---

