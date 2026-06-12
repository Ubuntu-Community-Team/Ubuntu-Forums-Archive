---
title: "An interesting situation with GRUB and password"
date: 2009-12-27
forum: General Help
---

### Post by lilrips1 on 2009-12-27
Here is the deal:

I received a lightly used netbook with Ubuntu on it, but I do not know the password. So, I learned that in order to change the password, I must go into the GRUB menu. However, when I boot, "Grub is loading... Press ESC to enter menu" does NOT appear. I believe this is die to the fact that in the "menu.lst" file, the timeoutsec value is 0. However, I am unable to change this value since I do not know the password and administrative actions are locked. I know I have grub legacy because the "menu.lst" file is indeed there.

Is my only option to reinstall Ubuntu?

---

### Post by taurus on 2009-12-27
Can you boot that netbook with an external USB CD or a thumbdrive?  You can then mount the partition where /boot resides and change the timeout from 0 to 3 (or whatever integer you want to use).

---

### Post by lilrips1 on 2009-12-27
Oh yes, I suppose that would work. Thanks!

---

