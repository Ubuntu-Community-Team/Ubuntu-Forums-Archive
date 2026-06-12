---
title: "Ubuntu 11.04 - Gnome Shell - Not Saving Icon Theme Or Wallpaper??"
date: 2011-07-11
forum: General Help
---

### Post by Roasted on 2011-07-11
I'm running Ubuntu 11.04 with Gnome3 PPA (Gnome Shell) on 3 different systems. Two work perfectly (custom desktop and CR-48 netbook) but the 3rd system, a Dell Latitude E5500 laptop, is having some weirdness.

Whenever I reboot, my wallpaper comes up blank and my icon theme is set to default Humanity-Dark. How can I change this? Once I select these items again, it's fine. But like I said, rebooting reverts it for some reason.

---

### Post by Groggster on 2011-07-11
If you have the wallpaper and icon theme on a disk or partition that is separate from the system disk/partition you might have mounting issues. Is this the case?

---

### Post by Jouke74 on 2011-07-11
Also check the rights of the files, if you copied them from USB they might have only root rights and not user rights. This problem works in both directions, so allow for everyone to read these files (user, group, everyone).

---

### Post by Roasted on 2011-07-12
> **Groggster said:**
> If you have the wallpaper and icon theme on a disk or partition that is separate from the system disk/partition you might have mounting issues. Is this the case?

My home and root directory are split, however I have no issues on my desktop, which has the same setup. I'm not seeing any mount issues. Everything else acts normal.

> **Jouke74 said:**
> Also check the rights of the files, if you copied them from USB they might have only root rights and not user rights. This problem works in both directions, so allow for everyone to read these files (user, group, everyone).

Permissions are root:root with 755. I tried 777 before, no difference. :confused:

---

