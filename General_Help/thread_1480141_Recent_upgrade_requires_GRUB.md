---
title: "Recent upgrade requires GRUB"
date: 2010-05-11
forum: General Help
---

### Post by madchine on 2010-05-11
When I installed lucid, I opted not to install GRUB as I leave that job to a small 'rescue' Arch Linux install somewhere else on the drive. However, some recent upgrade (I'm having difficulty figuring out which one exactly) claims to require the packages 'grub-pc' and 'grub-common'. 

I'm not sure but surely this is a mistake. Right? And if so, what are my options?  Does installing the packages automatically install grub (ubuntu-grub, that is) to the (insert word for that first part of the HD where the bootloader resides....?) Or will I have to manually tweak the package installation to avoid installing?

---

### Post by madchine on 2010-05-13
It seems like it was the kernel files. Locking them down allowed me to upgrade (everything but the kernel files). Surely surely surely, this 'dependency' is BS? And a bug, to boot...?

---

