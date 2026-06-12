---
title: "filesystems - mount - post ubu install"
date: 2006-04-03
forum: General Help
---

### Post by dotdot on 2006-04-03
hi folks...

my config ? dual boot win 2k ubu 510.

since installing 510  i've create a few other partitions .... from inside win2k

..I was wondering what do i now need to do to get ubuntu to see them.
(ie in media - i have no additional devices)



ie when i installed it picked up all the vfat fs'es which existed at the time... now ...i think it needs refresh (can't it do this automatically ?)..

fdisk -l shows all the net information.

can anyone advise on what I need to do to enable this ? 

I also created a ext 2 fs - which ubu can't see either... so the 
same question applies.

---

### Post by taurus on 2006-04-03
You have to edit your /etc/fstab to include that new partition.  If you tell me what it is, /dev/hda2, /dev/hda3, or whatever and the filesystem, fat32, then I can help you to add an entry in your /etc/fstab so that it would be mounted automatically upon boot...

---

### Post by Clopy on 2006-04-03
try this guide:

[http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

Let us know if you get confused in the process

---

