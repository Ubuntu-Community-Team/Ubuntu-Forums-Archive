---
title: "Strange thing with GRUB"
date: 2006-03-25
forum: General Help
---

### Post by YumZ on 2006-03-25
I am fairly new to Ubuntu (and Linux is general), but I was wondering why GRUB lists two different Ubuntu kernels:

Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-10-386 (recovery mode)
Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)

Shouldn't it only list one, and if so why is the other one there?

---

### Post by soce_32 on 2006-03-25
When you use apt to update your kernel, the old one is not removed.  You can have several different kernels installed on your computer, and pick which one to run at boot time.  If you update your kernel and find that something is suddenly broken, you can go back to an older, working kernel.

---

### Post by DOtSlaSHuCantCME on 2006-03-25
[QUOTE=YumZ]I am fairly new to Ubuntu (and Linux is general), but I was wondering why GRUB lists two different Ubuntu kernels:

Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-10-386 (recovery mode)
Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)

Shouldn't it only list one, and if so why is the other one there?[/QUOTE]


Hi....mines also list the same,i believe we can have more than 1,2,3 kernels installed but only one working,so installing new kernels can lead to having 1,2,3 kernels installed,which to some can be just taking up disk space.

---

### Post by YumZ on 2006-03-25
Disk space is a huge priority for me.  I only have a 6gb partition for Ubuntu, and only have 1gb left.  If I remove the second kernel, would I see a significant increase in disk space?

---

### Post by soce_32 on 2006-03-26
The kernels and modules only take up 65-70MB.  If you want to remove them completely, you can use the purge option to dpk/aptitude or choose completely remove in synaptic.

---

