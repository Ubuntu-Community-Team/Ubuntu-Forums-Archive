---
title: "EXT4 file recovery (urgent please)"
date: 2010-04-25
forum: General Help
---

### Post by Asem on 2010-04-25
Hello all;

i had an ext4 file system that was accidently deleted  while using gparted,
now the space it used is unallocated.

so before i do anything now,can you suggest a tool for recovery please.

---

### Post by idef1x on 2010-04-25
Try foremost. It helped me once with recovering a lot of photos.

---

### Post by jack_hmr on 2010-04-25
sfdisk can be used to edit the partition table if you can figure out where the partition started and stopped.

Testdisk might be able to find the deleted partition and fix/undo the problem by overwriting the new partition table with the old one.

A last resort would be to use Photorec (comes with Testdisk) to pull the files off. They would be sorted in a seemingly random way without a helpful directory structure. I have seen some scripts that will organize into file types.

---

### Post by Asem on 2010-04-25
Testdisk done it!!

you guys are the best
thank you...

---

