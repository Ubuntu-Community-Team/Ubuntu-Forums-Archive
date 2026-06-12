---
title: "Resized ubuntu and now issues booting XP"
date: 2009-12-07
forum: General Help
---

### Post by Jim55 on 2009-12-07
I resized my ubuntu partition and now when selecting XP at the GRUB menu I get the message "invalid signature".  I can bring up ubuntu and see XP in NTFS at SDB1.

Ubuntu was taking up all of the EXT partition ... the rest of my drive ... since its install.  I unallocated 824gb using gpart from the cd.  

How do I get around the  "invalid signature" and boot up XP again?

---

### Post by Jim55 on 2009-12-07
Bump

Someone must have seen this before ... your help would be appreciated as I would prefer not to have to reload XP.

---

### Post by Jim55 on 2009-12-09
This fixed my problem

sudo grub-mkdevicemap
sudo update-grub2

---

