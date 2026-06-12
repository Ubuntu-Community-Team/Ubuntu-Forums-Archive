---
title: "GNU GRUB version 1.98+20100804-5ubuntu3.3 keeps coming up when i turn on my laptop!!!"
date: 2011-09-01
forum: General Help
---

### Post by 1tnm1 on 2011-09-01
GNU GRUB version 1.98+20100804-5ubuntu3.3 keeps coming up when i turn on my laptop!
I really need some help!!
I installed the new update and then i had to restart my laptop so i did then it went to the login menu i pressed login then it froze!! So i restarted my laptop and this keeps coming up!

---

### Post by ajgreeny on 2011-09-01
So what is the problem;  can you still not get to login to the desktop?

What you show is a standard grub menu that appears when you have more than one operating system on a machine.  It is hard to be sure, but from the kernel version numbers, it looks as if you perhaps have, or have had Lucid on it, and have updated to Maverick.

If you only have the one OS on board it is unusual to see the grub menu appear, but you should be able to stop it from showing by editing /etc/default/grub.

See [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) for details of grub2

---

### Post by 1tnm1 on 2011-09-02
Thank You!!!

---

