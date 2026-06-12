---
title: "harddrive problems st3300831a"
date: 2010-01-10
forum: General Help
---

### Post by jimbean on 2010-01-10
should ubuntu see 
when i have a lockup and have to do a hard reboot in vista
and vice versa when i have a hard drive lockup in ubuntu , vista see`s it 
when i reboot
they both want to run system utilities
wheather i have lockup in ubuntu and try right after reboot to go into vista
and vice versa when i have a hard drive lockup in vista and reboot and go into ubuntu
ive replaced the mbr and ran scandisk defrag and gparted

---

### Post by dcstar on 2010-01-11
> **jimbean said:**
> should ubuntu see 
when i have a lockup and have to do a hard reboot in vista
and vice versa when i have a hard drive lockup in ubuntu , vista see`s it 
when i reboot
they both want to run system utilities
wheather i have lockup in ubuntu and try right after reboot to go into vista
and vice versa when i have a hard drive lockup in vista and reboot and go into ubuntu
ive replaced the mbr and ran scandisk defrag and gparted

How about replacing the faulty hardware before you lose **all** your data?

---

### Post by jimbean on 2010-01-18
the thing is you are right
but ive read that if you ghost or copy hard drive to hard drive
that the issues could be ghosted to the replacement drive
ive got vista setup like i want, i would reinstall ubuntu

---

### Post by warfacegod on 2010-01-18
I've never seen anyone post in verse before.

You can't transfer a hardware failure to another piece of hardware unless that failure is caused by a virus or something similar. I will warn you though, if you are using a none MS filesystem, ghosting your hard drive with MS based software can be unwise. For example: Norton Ghost has been known to read ext3 filesystems as corrupted ext2 and will then proceed on to trying to fix it and completely frag your files.

---

