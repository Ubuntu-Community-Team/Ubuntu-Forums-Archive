---
title: "few questions about install ubuntu with wubi"
date: 2010-08-19
forum: General Help
---

### Post by yaonatan on 2010-08-19
Hello!
1.can i install wubi with windows 7?
2.both of them will work ? the windows 7 will not hurt?
3.the windows 7 on "C" if ill install the wubi on "D" its fine?

---

### Post by M4he on 2010-08-19
1. Yes it works with Windows 7, I've tested that on my netbook.

2. It won't touch Windows 7 it only adds a boot entry for the vhd (virtual harddisk image), so you can choose what you want to start at bootup. You can later safely remove Wubi per control panel in Windows and it will delete the vhd and it's boot entry and Windows will be back to normal.

3. Yes, it should be. It only puts the vhd file on the D partition then.

Good luck and have fun with your Ubuntu installation on Wubi!

---

### Post by gadolinio on 2010-08-19
> **m4he said:**
> 
2. It won't touch windows 7 it only adds a boot entry for the vhd (virtual harddisk image), so you can choose what you want to start at bootup. You can later safely remove wubi per control panel in windows and it will delete the vhd and it's boot entry and windows will be back to normal.

3. Yes, it should be. It only puts the vhd file on the d partition then.

Good luck and have fun with your ubuntu installation on wubi!

+1

---

