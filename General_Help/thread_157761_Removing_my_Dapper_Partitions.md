---
title: "Removing my Dapper Partitions"
date: 2006-04-09
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-09
I am using breezy but how can I remove my dapper partition ? I broke it when I installed XGL and it currently is serving no purpose. I tried the GParted live cd but it didn't reconize my keyboard. Can I use the Ubuntu cd in some way ?

---

### Post by Celerex on 2006-04-09
YOu can delete the partition using fdisk if you'd like.

In a console window type: fdisk /dev/hd* (replace teh * with whatever letter the partition resides on. Typically this will be 'a')

Once in fdisk type: p (for printing)
Find the partition that is your drapper (counting starts from 1 where grub starts from 0 if that helps). Push 'd' to delete and then select the partition. Finally push 'w' to write the changes. You now have unallocated space.

You could also just mount this partition and rm -rf * the files... up to you.

---

### Post by plors on 2006-04-10
[QUOTE=MasterChief1234]<snip>
I tried the GParted live cd but it didn't reconize my keyboard. <snip>[/QUOTE]

It that case it's an old (OSS) custom to [file a bug]("http://gparted.sourceforge.net/bugs.php") so the developers of an app know about it and have a chance to fix it. :)

---

### Post by xXx 0wn3d xXx on 2006-04-10
Well, I can't mount or boot into the partition. Now it is "unallocated space." How can I remove it ? I tried gparted, qparted, rm -rf *, and fdisk.

---

### Post by plors on 2006-04-11
of course it's unallocated space, you removed the partitions so now you have unallocated space. Once you remove all matter from an environment you have a vacuum :cool: 

You can create new partitions in this unallocated space.

---

### Post by xXx 0wn3d xXx on 2006-04-11
Is there a way I can remove the Dapper kernels from my Grub menu ? Can I just gedit /boot/grub/menu.lst ?

---

