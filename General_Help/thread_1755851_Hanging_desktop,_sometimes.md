---
title: "Hanging desktop, sometimes"
date: 2011-05-11
forum: General Help
---

### Post by Atamisk on 2011-05-11
Been fighting this problem forever. 

Any time i try to start my computer from a cold state (off for 1+ hours), the first time i start it, it hangs and requires a SYSREQ reboot to restart it. When it hangs, all the window decorations disappear and the background vanishes. The main menu opens, but click on things does nothing. clicking shutdown only brings up the normal shutdown window with the text replaced with squares. 

Thought it was my hdd (i/o errors and for some reason the HDD remounts r/o at this point), but e2fsck shows no issue. 

Thought it may be an IRQ conflict, so i enabled MSI on all my PCI Devices. 

Thought it was the 'green' aspect of my WD Drive, so i set the spindown time to 5 hours using hdparm config file. startup messages printed to screen confirm it is working. 

Pulling out hair over this one!! Also, due to the numerous hard resets, the system is detecting a 'previous i/o error to the superblock'. Should recovering the SB from a backup be beneficial?

Thanks, 

-Aaron

---

### Post by Atamisk on 2011-05-13
anybody?

---

