---
title: "Auto-load script during wake up"
date: 2009-09-23
forum: General Help
---

### Post by BinaryMn on 2009-09-23
For the last several weeks, I've been fighting with an Atheros AR2413 wireless NIC to work properly with the ath_pci driver. Finally, after rebooting for the upteenth time last week, it worked.

However, I have to manually reload the ath_pci driver when I bring the laptop back from suspend/hibernate. To do this, I just made a file called wlan-reboot with the corresponding commands, marked it as an executable, and I run it manually when I turn my laptop back on.

How do I make this script run automatically, or is there a better way to reload the ath_pci driver when coming out of hibernat?

---

### Post by BinaryMn on 2009-09-23
Bump.

---

