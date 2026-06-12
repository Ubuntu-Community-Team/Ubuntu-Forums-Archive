---
title: "Accesing HD"
date: 2009-09-03
forum: General Help
---

### Post by Grumpy567 on 2009-09-03
I read that using Ubuntu i can access my hd and see my files that i have on windows. So if i do that would i be able to runa program that i have installed on windows. For example the game Combat Arms.

---

### Post by ackanao on 2009-09-03
It's possible but not recommended - if you want to use Windows programs just install them with Wine or dual-boot.

---

### Post by FlyingBuzz on 2009-09-03
> **Grumpy567 said:**
> I read that using Ubuntu i can access my hd and see my files that i have on windows. So if i do that would i be able to runa program that i have installed on windows. For example the game Combat Arms.
Right! You can run every program Wine supports. Several years ago when I was forced to use bual-boot mode (with that crappy vista) It [wine] had been firing up Counter-Strike very-very good directly from Vista's partition.
So, as I know, windows partitions are mounted automatically on startup in Ubuntu. Just find your executable and run it with Wine.

---

### Post by Grumpy567 on 2009-09-03
Thanks, according to what ive read Combat arms does not work properly with wine, so i guess i will dual boot.

---

### Post by ackanao on 2009-09-03
Of course it is possible to run them from Windows partitions but there are some risks of currupting your Windows installation:

[http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2]("http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2")

---

### Post by FlyingBuzz on 2009-09-03
> **ackanao said:**
> Of course it is possible to run them from Windows partitions but there are some risks of currupting your Windows installation:

[http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2](http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2)

The only way of possible corrupting of windows installation is mounting NTFS partition both for read and write.
Doing this with read only option will keep the partition safe and do almost everything simultaneously.

---

