---
title: "Can't unmount my hard drive"
date: 2009-09-23
forum: General Help
---

### Post by LinuxC4 on 2009-09-23
Hi,
I've installed ubuntu next to my windows xp each on a different partition of my hard disk
a icon of my windows xp partion appear on my ubuntu desktop and when i try to unmount 
a message appear and tell that i can't cz i don't have permission
can someone help me plz!
thx

---

### Post by hwttdz on 2009-09-23
So you don't have permission because you're a user, and not a super user.  You can open up a terminal and "sudo nautilus" and you should be able to right click and unmount from there.  You could also try install pysdm which gives you a lot of options in mounting or unmounting.

You might also just not want it to show on the desktop.  In that case open up a terminal or synaptic and install gconf-editor and look under apps->nautilus->desktop and uncheck volumes visible, note this will also prevent say a cd from showing up on the desktop.

---

