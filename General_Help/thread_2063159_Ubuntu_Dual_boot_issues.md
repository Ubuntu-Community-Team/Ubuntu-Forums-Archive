---
title: "Ubuntu Dual boot issues"
date: 2012-09-26
forum: General Help
---

### Post by Jpredshift on 2012-09-26
Apologies if this has been covered elsewhere, been struggling to find a solution.

Ubuntu 12.04 & Windows 7 dual boot, all running fine until I set (via windows, my computer properties) Ubuntu as the default OS. Now the System boot loader flashes up momentarily and selects Ubuntu, which is great until I want to boot Windows 7.

Pressing shift at Ubuntu startup brings up the grub boot options, but there's no Windows 7 option.

Any help would be appreciated! Let me know what info you need.

Cheers

---

### Post by CCgirl6690 on 2012-09-26
you need win 7 disc , boot it up then click on fix windows then theres a little commands you gotta put in and your win7 is back up again

---

### Post by oldfred on 2012-09-26
Welcome to the forums.

This sounds like a wubi install that uses the Windows boot loader and has the initial boot selection in Windows BCD file.

As CCgirl6690 you need to use the Windows repair CD or USB or boot into Windows repair console (f8 ) and use bcdEdit.

If you find you like Ubuntu and are using it a lot, you may want to consider a full partitioned install.

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

