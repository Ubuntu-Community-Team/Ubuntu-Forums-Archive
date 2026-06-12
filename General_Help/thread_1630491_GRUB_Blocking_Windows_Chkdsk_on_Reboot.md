---
title: "GRUB Blocking Windows Chkdsk on Reboot?"
date: 2010-11-25
forum: General Help
---

### Post by iEthan on 2010-11-25
Hi. I'm running a dual-boot with Ubuntu 10.10 and Windows XP with GRUB. There are a few corrupt files on my XP filesystem, so I scheduled Windows to run Chkdsk on restart. I restart, select Windows in GRUB, and the screen shows saying it will run Chkdsk, press any button to cancel. Without me touching any buttons, it cancels it.

I think GRUB may be the issue, but I could be wrong. Any help would be appreciated.

---

### Post by dino99 on 2010-11-25
dont believe that grub would be blamed, its a bootloader nothing else. To fix xp boot on its cd or use the rescue mode.

---

### Post by lmarmisa on 2010-11-25
Maybe this is normal. Sometimes a reboot is needed after a chkdsk repair procedure.

Are you able to boot into XP now?.

---

### Post by iEthan on 2010-11-25
@dino99: Thanks for your help, that was just a guess on my part.

@lmarmisa: I have been able to boot into XP, it's just that it automatically cancels the Chkdsk every time I boot into it.

---

### Post by lmarmisa on 2010-11-25
Maybe you have a problem with with the filesystem (NTFS or FAT) of your XP, but I believe that it is not related to Ubuntu or GRUB.

---

### Post by dino99 on 2010-11-25
dont remember well about Chkdsk (winblows gone away for a while now on my end :) ) but:

chkdsk -h  will let you know about available settings (or help chkdsk, or chkdsk ? )

---

