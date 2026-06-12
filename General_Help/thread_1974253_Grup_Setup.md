---
title: "Grup Setup"
date: 2012-05-05
forum: General Help
---

### Post by sinamorawej on 2012-05-05
Hi

I just finished installing ubuntu 12.04 and windows 7 on two separate sata drives. I kept each installation isolated (ubuntu installed first on sata1 and hard drive was unplugged when windows was installed on the second drive, sata2) in order to reduce complications.

My question is how do I configure grub with this setup? at the moment my machine boots straight into linux without the grub menu.


Thanks

---

### Post by sisco311 on 2012-05-05
Open a terminal and run:
```
sudo update-grub
```

Ubuntu should recognize Windows and add it to the Grub menu. If the Grub menu doesn't show up at boot, then try to hold down the Shift key dooring the boot.

---

### Post by sinamorawej on 2012-05-06
cool - thx

---

