---
title: "problem with adding XP to Grub2"
date: 2011-01-15
forum: General Help
---

### Post by Seepgood on 2011-01-15
I'm running Kubuntu 10.4. I cloned an old xp installation into the first primary partition on my disk and I was trying to add it to grub2. I can access the files when I mount it which means that the xp filesystem is working fine. When I do an update-grub though it doesn't detect it. I think that the problem is related to the fact that I cannot find a boot.ini file into the xp installation. I've read some guides but they didn't help much. Any solutions?

PS. To recreate the boot.ini I have to do a fix with the windows installation cd. I can't do that before I boot into windows though.

---

### Post by Quackers on 2011-01-15
update-grub won't pick up the XP installation until boot.ini is present afaik. You need to repair the Windows bootloader, get Windows booting, then re-install grub.

---

