---
title: "How to update GRUB on Ubuntu 10.04?"
date: 2010-05-15
forum: General Help
---

### Post by dineshrathod2216 on 2010-05-15
Hi guys, I recently installed Ubuntu 10.04 via Wubi installer. When I updated it, I got a pop up asking me to Continue without updating grub. So I continued and I see that I still have the old GRUB version. How to update to the latest version of GRUB?

Edit: when I boot, at the top I see : "GNU GRUB Version 1.98-1ubuntu5"
Then below I see ubuntu,linux 2.6.32-22-generic. 
Is that the latest version?

Thanks,
Dinesh.

---

### Post by oldfred on 2010-05-15
You have the current version.

grub legacy is 0.97
Karmic used either grub legacy or grub2 (1.97 beta4)
Lucid uses grub legacy or grub2 (1.98)

upgrades kept the old version of grub, new installs used the current version of grub2 (which is no yet at version2).

---

### Post by dineshrathod2216 on 2010-05-18
> **oldfred said:**
> You have the current version.

grub legacy is 0.97
Karmic used either grub legacy or grub2 (1.97 beta4)
Lucid uses grub legacy or grub2 (1.98)

upgrades kept the old version of grub, new installs used the current version of grub2 (which is no yet at version2).
Thanks for the info. :D

---

