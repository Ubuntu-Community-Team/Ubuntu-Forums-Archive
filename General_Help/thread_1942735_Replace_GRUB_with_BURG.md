---
title: "Replace GRUB with BURG"
date: 2012-03-18
forum: General Help
---

### Post by Subidubi32 on 2012-03-18
How could I write the BURG to MBR? If something go wrong can I restore grub2 from the live CD? I would like to try BURG because it's graphical boot menu, but I can't run it, only emulate it, when Ubuntu runs already. I tried to reinstall it so many times, but if I turn on my computer the GRUB2 comes up. I did everything the same, as the installation guide, but it isn't working.

---

### Post by Subidubi32 on 2012-03-18
Found other guide.

---

### Post by The Cog on 2012-03-18
How? I'm curious to know. Do you have a link?

---

### Post by dcstar on 2012-03-19
> **Subidubi32 said:**
> How could I write the BURG to MBR? If something go wrong can I restore grub2 from the live CD? I would like to try BURG because it's graphical boot menu, but I can't run it, only emulate it, when Ubuntu runs already. I tried to reinstall it so many times, but if I turn on my computer the GRUB2 comes up. I did everything the same, as the installation guide, but it isn't working.

```
sudo dpkg-reconfigue burg-pc
```
Select your hard drive as the boot loader destination.

---

