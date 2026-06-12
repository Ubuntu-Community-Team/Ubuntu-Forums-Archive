---
title: "chroot environment booting"
date: 2009-10-27
forum: General Help
---

### Post by Psycho.mario on 2009-10-27
I am always breaking my installations one way or another and causing myself to reinstall. I was wondering, would it be possible to do a fresh install, copy all the files from / to /var/chroot/ and add an option to grub to use the files in /var/chroot as the OS? So if i then broke the system, i could boot the original grub option, wipe /var/chroot, and copy everything again? I have a 300gb hard disk and installs are usually less than 5gb so space is not a problem.

Thanks in advance

---

### Post by Psycho.mario on 2009-10-28
Bump

---

### Post by Psycho.mario on 2009-10-28
As no one seems to have any idea as to whether this will work or not, i will try it tomorrow. I am planning on doing a clean install with the release of karmic. So far i have realised that the /var/chroot/boot/grub folder does not need to exist, neither does the /var/chroot/etc/fstab. I will duplicate all of the lines in the /etc/fstab, with the bind option to the chroot root. 

e.g
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/fd0        /var/chroot/media/floppy0  auto    bind,rw,user,noauto,exec,utf8 0       0
```

I am not sure that this will work, but i think it will. I will do the same for procfs, tmpfs and all the other fs' in /etc/fstab.
Anyone got any other ideas as to what i would need to do?

Thanks

---

