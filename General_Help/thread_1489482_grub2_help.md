---
title: "grub2 help"
date: 2010-05-21
forum: General Help
---

### Post by bone2006 on 2010-05-21
I'm simply trying to remove old kernels and second rename things that are on the list.  It used to take me 10 seconds with grub1, but having some difficultly with grub2.

So far I went into /boot/ and removed the old kernels and then did a sudo update-grub2 and it seemed to remove all the old kernels from the list.  Is this the best way or doing it or any issues on doing it this way?

Second I just want to rename what boots up like
Ubuntu 2.6.32-22-generic to something else.  I keep read not to modify the grub.cfg, but not sure what to do?

I poked around the files in  /etc/grub.d/ , but not sure what to do?

---

### Post by Ad@m on 2010-05-21
Read this instead,

Modify the grub.cfg file

:)

---

### Post by wilee-nilee on 2010-05-21
There is a thread  going right now that discusses changing the kernel names you will have to find it though. I don't think it has a thread name associated with changing the read line in grub.

---

