---
title: "stars on plymouth fade-in theme"
date: 2010-05-21
forum: General Help
---

### Post by lavinog on 2010-05-21
A while back I switched the boot theme to fade-in using the command:
```

sudo update-alternatives --config default.plymouth

```

Today I booted and a bunch of stars appeared across the screen.  Does anyone know why it did this?  Is this some sort of easter egg?

---

### Post by lavinog on 2010-05-21
I just rebooted, and didn't get them this time.
I did however notice that plymouth-log-viewer showed a disk check for one of my disks, so I wonder if it has something to do with that.

---

### Post by lavinog on 2010-05-22
Noticed it again:
```

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda6: clean, 173978/708528 files, 885969/2833456 blocks
/dev/sda5: clean, 213/58232 files, 45950/232876 blocks
/dev/sda9 has been mounted 26 times without being checked, check forced.
/dev/sda9: 23224/1597440 files (1.5% non-contiguous), 3745461/6377797 blocks
 * Starting AppArmor profiles       [160G modem-manager: Loaded plugin MotoC

```
It looks like it happens with fsck...how funny.

---

