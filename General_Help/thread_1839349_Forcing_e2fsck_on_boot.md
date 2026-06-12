---
title: "Forcing e2fsck on boot"
date: 2011-09-05
forum: General Help
---

### Post by hwttdz on 2011-09-05
In my dmesg I'm seeing a few 

[   10.303681] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended

warnings.  And I thought, I should probably do that, a little bit of googling turned up that I should be able to force a check by "touch /forcefsck" and then restarting.  But no dice.  Anyways I'd really much rather run this at startup than by unmounting drives.  Any suggestions?

---

### Post by dino99 on 2011-09-05
hm, it should start itself via cronjob (ubuntu default)

sudo shutdown -r now

will force it on next boot.

---

### Post by hwttdz on 2011-09-05
I've done the minimal install so a bunch of ubuntu defaults don't hold true. 

I had made a mistake in the fstab, 6th column should be non zero to allow checks.  Oops.

---

