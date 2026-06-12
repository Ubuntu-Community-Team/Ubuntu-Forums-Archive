---
title: "New updates just broke my ubuntu"
date: 2011-06-28
forum: General Help
---

### Post by mbezik on 2011-06-28
I just woke up and found an update dialogue box with a few new updates, new linux headers etc, upon installing the said updates and restarting as informed to do so - now my 10.10 wont go past the non gui stage - if i run the previous release in my grub list it fires up the same as b4 but the new release wont start the desktop

---

### Post by dino99 on 2011-06-28
so purge then reinstall the latest kernel; is it a genuine one ?

---

### Post by hawthornso23 on 2011-06-28
What graphics driver were you using. 

This often happens when you have a proprietary graphics driver installed. These drivers involve a kernel module which can get nuked during a kernel upgrade. If that happens the graphics driver will stop working leaving you in a text login. The fix is to reinstall your graphics driver.

Good Luck

---

