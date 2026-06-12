---
title: "Boot Menu Query"
date: 2011-08-24
forum: General Help
---

### Post by deepaknet on 2011-08-24
Dear Ubuntu Team,

I have recently upgraded my box to Ubuntu 11.10. The bootmenu shows as below:

[http://www.mediafire.com/?teanff8gbn8pl85](http://www.mediafire.com/?teanff8gbn8pl85)

Is there a way to remove the older linux versions?

---

### Post by Quackers on 2011-08-24
You can uninstall the old kernels using synaptic (just enter their numbers in the search box and when they appear in the main window right-click them and select mark fro complete removal0. There will be 3 entries for each kernel (but you may only need to mark 2 for removal). Then click on the green tick in the toolbar to apply the changes.
Remove as many kernels as you wish in this way - but definitely not the current one!
People advise that the current one and one previous kernel be left in the system (for possible recovery purposes).
Once the chosen kernels are removed open up a terminal and run ```
sudo update-grub
```to clean up the grub menu.

---

