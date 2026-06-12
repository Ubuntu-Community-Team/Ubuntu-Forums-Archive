---
title: "undelete logical partition"
date: 2012-09-13
forum: General Help
---

### Post by ritti on 2012-09-13
Hi, I just wanted to reinstall windows next to ubuntu (as it was before)
and deleted the windows partition. The problem is that my ubuntu partition was a logical one and the windows the primary one. I use Windows only for gaming so all my important files were on the ubuntu partition. As i deleted the windows partition, the windows installer deleted my ubuntu partition too because its a logical partition. Is there a way to get the files back? I haven't done anything after deleting the partitions so I didn't write to the hdd since that.
I hope somebody can help me
Thx in advance
Ritti

---

### Post by SlugSlug on 2012-09-13
I'd start with testdisk and re-write your partition table but wait for more answers / a guide

---

### Post by ritti on 2012-09-13
Tank you for your answer, I tried it with testdisk but it only recovered the windows partition :( I get the error ext4-fs no journal if I try to mount the ubuntu partition.
After trying fsck and clearing some inodes I canceled it because I assume that it would screw up my whole partition. What should I do?
I even tried parted with the rescue option but it didnt find anything.

---

### Post by tienlbhoc on 2012-09-13
sometimes, partition table is error, backup data in other pc (via LAN with samba) and remove all partition table and regenerate it.
In a few years ago, I have a partition error and after re ghost windows, all data lost :(.
Now I am using dropbox to backup important data in cloud

---

