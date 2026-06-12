---
title: "Dual Boot menu help please"
date: 2009-10-06
forum: General Help
---

### Post by DirtyDawg on 2009-10-06
Hi i have windows 7 and Ubuntu 9 installed in a dual boot setup.
All is fine and i have the boot options available, however -
it defaults to ubuntu with a 9 second timer.
I would like to have win7 as the default option since i am still
new to linux and use 7 more at the moment.

Is there a Graphical tool to configure boot menu as i am not
very confident and dont know how to adjust the options,
thanks in advance to anyone who responds. :)

---

### Post by CharlesA on 2009-10-06
Check this out:

[http://www.linuxforums.org/forum/misc/8423-grub-default.html](http://www.linuxforums.org/forum/misc/8423-grub-default.html)

Looks like you need to edit /boot/grub/grub.conf and change the number listed under "DEFAULT" to the one you want.

Not sure if there's a GUI for this one in the grub menu or not.

---

### Post by Giblet5 on 2009-10-06
"Ubuntu 9" is less helpful than you think.

9.04 or 9.10? It's VERY different between the two.

---

### Post by ajgreeny on 2009-10-06
If you are using jaunty (9.04) you can install and use startup-manager to do exactly what you want.  I don't think it is very successful with grub2 now used in ubuntu 9.10, but may work to some extent.  As far as I'm aware, using Win7 does not complicate startup-manager's use.

---

### Post by Giblet5 on 2009-10-06
For legacy grub, kgrubeditor is excellent.

For grub2 (9.10 aka Karmic), there are no good gui tools yet.

---

### Post by DirtyDawg on 2009-10-06
Thanks for the fast response and reply guys, very helpfull :P

---

