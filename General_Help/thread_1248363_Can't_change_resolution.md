---
title: "Can't change resolution"
date: 2009-08-24
forum: General Help
---

### Post by arandomkiwi on 2009-08-24
So I installed ubuntu. Ran it, and resolution is 800x600. That was the max. After configuring the xorg.conf under /etc/X11/, I managed to add a new resolution (1280 x 1024). That is far to big. 800x600 is to cramped. Any suggestions on fixing up this mess

(I'm actually using 9.04 unlike what it says on the left. I will deal with that ;))

---

### Post by P4man on 2009-08-24
eh.. change that 1280x1024 in to 1024x768 in xorg.conf ?

---

### Post by wojox on 2009-08-24
Are you stuck @ 1280 x 1024 and need to reset xorg.conf?
Did you check System > Administration > Hardware Drivers to see if your graphics driver needed to be activated?
What graphics card are you using?

---

### Post by Granny_Geek on 2009-08-24
That problem is usually fixed for me once I install the Nvidia drivers needed to get Compiz working. Once I do that & let the updates complete, then restart...correct resolution is automatic for me:-)

---

