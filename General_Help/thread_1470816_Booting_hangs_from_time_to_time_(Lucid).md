---
title: "Booting hangs from time to time (Lucid)"
date: 2010-05-03
forum: General Help
---

### Post by cguy on 2010-05-03
I started out with Kubuntu RC, then installed ubuntu-desktop and updated all the way to the current state of packages.

Anyway, from the moment I installed the RC, from time to time the boot splash appears, the dots light up/turn off and then the booting hags. No key seems to work.
I the do a hard reset and everything works just fine.

Any idea why this happens?


As not to open another thread:
- how can I see the Ubuntu splash screen? (currently I can see the Kubuntu one)
- how can I turn the splash off and have it boot in text mode?


Thank you!

---

### Post by dino99 on 2010-05-03
is your hardware driver recognized and activated ?
(system admin hardware driver)

sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure jockey

---

### Post by cguy on 2010-05-04
Those commands didn't fix it as it just happened again.

I am not using the proprietary drivers, just Nouveau.

---

### Post by cguy on 2010-05-09
It was Nouveau who caused the hanging.
I activated the proprietary driver and everything is OK now.

---

