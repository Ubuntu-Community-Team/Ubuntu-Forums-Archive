---
title: "set the grub timer to human reflexes?"
date: 2009-12-12
forum: General Help
---

### Post by FreezWay on 2009-12-12
I need to set the grub countdown thingy so someone with human reflexes can select the correct kernel version. how do i do this

---

### Post by justin_guerin on 2009-12-12
If you're using grub2, per [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275), edit /etc/default/grub and change the GRUB_TIMEOUT.  The default is 10 seconds.

If you're using grub 1.x, then edit /boot/grub/menu.lst and set it there.

Justin

---

### Post by deathbyswiftwind on 2009-12-13
> **FreezWay said:**
> so someone with human reflexes can select the correct kernel version

:lolflag: Loud and clear on that one! On my desktop I installed the ati driver without knowing it wouldnt work on 9.10 and I needed to get into recovery mode... after about 20 minutes of anger I finally got it. That was probably the most frustrating time Ive ever had so trust me I feel your pain!

---

