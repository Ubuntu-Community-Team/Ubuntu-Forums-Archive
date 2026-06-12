---
title: "Dual boot question"
date: 2010-10-17
forum: General Help
---

### Post by mdmorash on 2010-10-17
Hello, I am currently running a dual boot with windows 7 and Ubuntu 9.10. Is there a way to get rid of the windows 7 partition without redoing the hard drive? I know how to delete the second partition and then do a FixMbr in windows. Is there a way to do that in Ubuntu?

---

### Post by sikander3786 on 2010-10-17
You don't need to the fixmbr equal i.e, reinstall Grub in Ubuntu. Just delete the Windows partition using your favorite Partition Manager (mine is gparted) and run

```
sudo update-grub
```

afterwards to get rid of the Windows entry from Grub menu.

If you are still not sure what to do, post the output of

```
sudo fdisk -l 
```

---

### Post by mdmorash on 2010-10-17
Sweet. Thanks. I love how everything is so much more straight forward in Linux. :guitar:

---

