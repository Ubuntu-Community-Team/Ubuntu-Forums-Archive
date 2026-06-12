---
title: "How To remove Some unused entries in grub2 ?"
date: 2010-06-22
forum: General Help
---

### Post by varexnet32 on 2010-06-22
hello i have an entry in grub that i don't use at all "Windows recovey "  and i want to know if there is a way to remove it or just hide it .....
+
i have an other problem is
grub confuses some partitions names so is there a way to rename them

---

### Post by sisco311 on 2010-06-22
[thread=1287602]Grub 2 Title Tweaks Thread[/thread]

---

### Post by Mark Phelps on 2010-06-22
> **varexnet32 said:**
>  ... I have an other problem is
grub confuses some partitions names so is there a way to rename them

If by "names" you mean IDs like /dev/sda1, the answer is no.  Those aren't partition names, they are device IDs.

If you mean the actual "label" of the partition, you can change that to be a different text string.

---

### Post by varexnet32 on 2010-06-22
No i mean with that : 
my menu should look like this : 
- ubuntu ...
- something else..
-vista recovery (dev/sda2) --> it must takes me to my recovery 
-vista (dev/sda1) --> it must takes me to my vista

but it looks like this : 

- ubuntu ...
- something else..
-vista (dev/sda1) --> But this takes me to Recovery
-vista recovery (dev/sda2)  --> But this takes me to vista

---

