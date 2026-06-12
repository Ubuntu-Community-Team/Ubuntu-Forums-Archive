---
title: "Grub only works when booting with disc"
date: 2006-05-12
forum: General Help
---

### Post by lastrite on 2006-05-12
After installing Ubuntu (dual boot with windows) i'm having issues with my pc directly booting grub. I get the error 'Invalid operating system!' but found that if I boot with my xp cd and let it time out when it asks for a keypress the Grub menu loads fine and I can boot into both operating systems :confused:  

Both are installed on a Sata hd running on single stripe mode in a raid (to get windows to detect it), I dont know if that has any baring on this problem.

Please help! :(

---

### Post by dg_w on 2006-05-12
Ok
Once you have managed to get into Ubuntu

Sudo grub-install /dev/hda  (change /hda to what ever the first partition is)

---

### Post by lastrite on 2006-05-12
Thanks! It worked :D

---

