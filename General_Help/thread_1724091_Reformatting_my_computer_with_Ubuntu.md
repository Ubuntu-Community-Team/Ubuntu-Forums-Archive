---
title: "Reformatting my computer with Ubuntu?"
date: 2011-04-07
forum: General Help
---

### Post by kthompso09 on 2011-04-07
I lent my secondary laptop to a friend for a school semester and he downloaded ubuntu onto it.  Now the laptop wont work properly, and because I am not familiar *at all* with Linux, I do not know how to get rid of Ubuntu and put windows back onto it.  I assume that I need to reformat the computer, but the mouse pad and keyboard do not work.  How do I go about doing this? Please help - I'm so lost

---

### Post by Meta1203 on 2011-04-07
You probably won't like this, but if you have a dual boot scheme, you need to get a Linux Live CD, such as GParted, Ubuntu, or another Live CD that supports partition editing. Then, simply boot from it and delete the Ubuntu partition. After that, reinstall the window's boot loader using the windows install CD. If it was not a dual boot, then just reinstall windows using the install CD. It is that easy!

---

### Post by kthompso09 on 2011-04-07
How do I know if it was a dual boot scheme?  Is that when there is Windows AND Ubuntu both on the computer?

---

### Post by linuxuser12345 on 2011-04-07
Go on Ubuntu.com and read about Ubuntu a little bit, and try installing a different version of Ubuntu (like 10.04, LTS) and try it out! I think you will like it if you give it a chance! :)

---

### Post by JKyleOKC on 2011-04-07
> **kthompso09 said:**
> How do I know if it was a dual boot scheme?  Is that when there is Windows AND Ubuntu both on the computer?Yes.

If you see a menu when you power the machine up that lists Windows first and Ubuntu on the second line, your friend installed Ubuntu using the "wubi" package and all you have to do is choose Windows, then go to add/remove programs and remove the ubuntu program.

If you see a menu that lists Ubuntu first, and Windows at the bottom of the menu, it's a dual boot installation on separate partitions, and the advice of the previous poster is correct. Remove the Ubuntu partitions, and repair Windows from the recovery CD.

However if you do NOT see any menu when you power up, then it's not a dual boot installation. Using your Windows recovery CD should take care of reformatting and re-installing Windows, unless it's an HP box and your friend wiped out its recovery partition. If that happened, you will need to order recovery disks from HP, or buy a retail copy of Windows!

---

