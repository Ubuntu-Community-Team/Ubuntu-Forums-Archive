---
title: "Grub Has Multiple Ubuntu links"
date: 2011-02-26
forum: General Help
---

### Post by TheBiggoronsword on 2011-02-26
When my laptop boots it shows the Grub menu, and it works fine except that every time I run an update, it add another ubuntu entry to the list, including regular and safe mode.  Is there a way to get rid of the old entries? 

     Any help would be appreciated.  Thanks

---

### Post by TeoBigusGeekus on 2011-02-26
These entries are the kernels currently installed on your system.
You only need the latest and the one before the latest (for security reasons, in case something goes wrong with the newest kernel).
Open Synaptic (Administration>System>Synaptic Package Manager).
Search for linux-image.
Keep the two newest images; the rest-right click them and select completely remove.
Open terminal and give
```
sudo update-grub
```
to update your grub (dah) and you're done.

---

### Post by TheBiggoronsword on 2011-02-26
Ok thanks. It worked fine.

---

