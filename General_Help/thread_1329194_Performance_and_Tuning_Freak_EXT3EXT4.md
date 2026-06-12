---
title: "Performance and Tuning Freak EXT3/EXT4"
date: 2009-11-17
forum: General Help
---

### Post by ricardo.gloe on 2009-11-17
I don't know about you, but I certainly consider myself a performance and tuning freak. I'm always on the lookout for something I can do to increase boot speed, application start-up or anything, even f the gain will be minimal.

What I miss the most since I migrated to Ubuntu KK 9.10 is the ext3 and ext4 tuning options we had with grub and fstab. 

Since Grub2, I haven't been able to apply the data=writeback option, I guess because I don't know where to put that rootflags=data=writeback, which used to go in menu.lst. It used to go under defoptions but I have no idea where it goes in grub2.

---

### Post by CHaoSlayeR on 2010-03-20
Just if you didn't find out where it goes:

Default boot options go into /etc/default/grub. The benefit of this is that you don't have to specify it for each kernel. It gets applied to all installed kernels when you run update-grub.

---

