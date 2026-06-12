---
title: "VirtualBox kernel module breaks after each kernel update"
date: 2010-01-06
forum: General Help
---

### Post by nocturn on 2010-01-06
I'm running Virtualbox from the Sun website (need the USB support) and it breaks after each kernel update.

The problem is that I installed a lot of Ubuntu systems for transitioning windows users with Windows in virtualbox to ease the migration but I have to rerun vboxdrv setup after each kernel patch.

Does anyone know a way to avoid doing this?

---

### Post by zvacet on 2010-01-07
I just reinstall Vbox after every kernel upgrade.I think reason is kernel headers.I also can be wrong and I would like to know if there is better solution for that.

---

### Post by nocturn on 2010-01-07
> **zvacet said:**
> I just reinstall Vbox after every kernel upgrade.I think reason is kernel headers.I also can be wrong and I would like to know if there is better solution for that.

Thanks, but the problem is that my non-technical friends don't have root on their boxes... so I need to figure out something automated.

---

