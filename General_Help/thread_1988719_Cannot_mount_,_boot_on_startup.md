---
title: "Cannot mount /, /boot on startup"
date: 2012-05-28
forum: General Help
---

### Post by l07 on 2012-05-28
I just installed the latest e2fs tools (sudo make install) to  update the existing version on 10.10. However, upon restarting the  computer it said that it cannot mount some partitions (like /, /boot)  and mentions fsck. The boot process appears to stop there. Of course,  the system loaded enough code from the hard drive to print those  messages so it must be able to access at least /boot. So I'm not clear  as to what those messages really indicate.
  I can get the exact messages if you could indicate how to shutdown  the pc after doing so, because currently I'm using power button hold,  and I think that's suboptimal.
  Could my update be the problem? How do I fix this?
  Perhaps it can be fixed by uninstalling the new e2fs tools. I would  cd to their directory and run make uninstall. However I don't know how  to do that without having the system boot. Maybe by using a live cd and  chroot but I'll have to look up the exact steps.
  Please answer as soon as possible.

---

