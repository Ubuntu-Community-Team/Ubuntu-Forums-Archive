---
title: "Grub error"
date: 2010-04-15
forum: General Help
---

### Post by ihyaked on 2010-04-15
i had full installation of ubuntu on my computer n i wanted to install win 7 after it.so i formatted ubuntu with live cd and when inserted win 7 dvd to install it ,it says loading grub please wait .....and then it displays error loading grub....
anybody please help how can i do it

---

### Post by mcduck on 2010-04-15
> **ihyaked said:**
> i had full installation of ubuntu on my computer n i wanted to install win 7 after it.so i formatted ubuntu with live cd and when inserted win 7 dvd to install it ,it says loading grub please wait .....and then it displays error loading grub....
anybody please help how can i do it

Make sure your computer is set to boot from CD first, and that the Windows disk you are trying to use is fine.

If you even get as far as Grub, then there is problem either in the Windows disk, or the BIOS boot order, as Grub is loaded *after* the point when the Windows disk is supposed to be started.

(Grub error is of course result from formatting the Ubuntu partition, as only the first stage of Grub is installed in your hard drives MBR, the rest was on that Ubuntu partition.. But this has nothing to do with problems booting the Windows install disk.)

---

