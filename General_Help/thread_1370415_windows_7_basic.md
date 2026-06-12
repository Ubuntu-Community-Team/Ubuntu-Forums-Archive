---
title: "windows 7 basic"
date: 2010-01-02
forum: General Help
---

### Post by mussiexxx on 2010-01-02
when i installed ubuntu i deleted windows 7 basic now i can"t load it i get a message error and i don"t want to uninstall ubuntu for windows and with wine i get error how to get windows 7 to run

---

### Post by starcraft.man on 2010-01-02
I'm not sure I follow, are ya saying you told the installer to use the whole disk rather than just free space and thereby removed all of Windows7 ? If so, it's you know.... gone. You'd have to reinstall it to a new partition, then restore GRUB.

Unless your saying you just overwrote the bootloader then you just need to fix up GRUB to detect it. 

Please make it clear, your message wasn't easy to understand.

---

### Post by Mark Phelps on 2010-01-02
If I understand what you're asking, you're trying to install Win7 Basic using Wine?

If that's true, you can't do that.  Wine can only be used to install Windows programs, not Windows itself.

If I misunderstood what you're trying to do, please explain it in clearer terms.

---

### Post by starcraft.man on 2010-01-02
> **Mark Phelps said:**
> If I understand what you're asking, you're trying to install Win7 Basic using Wine?

If that's true, you can't do that.  Wine can only be used to install Windows programs, not Windows itself.

If I misunderstood what you're trying to do, please explain it in clearer terms.

Oh geez, I didn't even see that reading. If you do want a copy of Windows inside ubuntu have a look at virtual machines (google for understanding) and try virtualbox (available in software centre). You can install windows inside that.

It won't however offer the same performance as local install, you can't do rendering for instance since you've limited access to local GPU.

WINE can only install programs, not Windows. VMs offer complete virtualization but suffer performance compared to a real install on some tasks.

---

