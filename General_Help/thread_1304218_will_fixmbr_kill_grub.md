---
title: "will fixmbr kill grub?"
date: 2009-10-29
forum: General Help
---

### Post by tmac503 on 2009-10-29
I am dual booting XP and Ubuntu 9.04 but a little while ago my XP blue screened and I can't seem to restore windows (even in safe mode I receive a blue screen before I can finish booting). However, grub still loads and I can boot into Ubuntu normally. After doing a little reading, it seems like one potential way to solve my XP issue is to boot off of my XP install cd and run fixmbr.
Is there any risk of this command screwing up my bootloader? I'd hate to lose access to both of my partitions in one night!

---

### Post by unmole on 2009-10-29
If you have the Ubuntu live CD (Or any linux live CD for that matter). You can fixmbr from the Windows CD and then fix grub from the Linux live CD.

---

### Post by unmole on 2009-10-29
After you have fixed you mbr from windows, boot into the live CD and do a
```
$ sudo grub
grub> find /boot/grub/stage1

```. You will find sometjing like (hd0,0). Use this and do a
```
 grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```

---

### Post by Mr_Congeniality on 2009-10-29
By the way, you should type in FIXBOOT and FIXMBR in the windows recovery console, and do that twice to make sure.  That's what I always do, then reinstall GRUB.

---

