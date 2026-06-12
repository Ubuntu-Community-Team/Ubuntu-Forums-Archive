---
title: "Stuck at Grub prompt after installing windows"
date: 2009-12-30
forum: General Help
---

### Post by N_Nick on 2009-12-30
I installed windows the other day and it messed up my mbr. I tried restoring grub the usual way from a live cd but after rebooting i'm stuck at a grub prompt where i have to manually select the kernel and boot.

Any thoughts?

---

### Post by pfranks on 2009-12-30
Check your grub configuration. It sounds like your default may be broken or missing.

---

### Post by QLee on 2009-12-30
[QUOTE=N_Nick]I installed windows the other day and it messed up my mbr. I tried restoring grub the usual way from a live cd but after rebooting i'm stuck at a grub prompt where i have to manually select the kernel and boot.

Any thoughts?[/QUOTE]

My first thought was that you didn't get a good GRUB re-install.

You would probably improve you chances of getting help if you explained exactly what steps you used, just stating "restoring grub the usual way" doesn't give much to help troubleshoot, what is the "usual" way for you?

Was it a 9.10 live CD or some other version?

---

### Post by phillw on 2009-12-30
Hi, head over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you did a fresh install of 9.10, then you're on Grub2. 
If you Updated from 9.04 to 9.10, or you are running on a version before 9.10 then you're on Grub Legacy.

Regards,

Phill.

---

