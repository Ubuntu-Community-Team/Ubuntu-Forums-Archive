---
title: "Can't have more than 4 primary partitions?"
date: 2006-02-01
forum: General Help
---

### Post by Curlydave on 2006-02-01
Why can't I have more than 4 primary partitions?

I have a WindowsXP partition for games and primary use.

I have a Ubuntu partition for experimenting.

I have a shared partition formatted in fat32 that my music and documents stay on so I can access them in Win and Linux.

I have an extra partition that Ubuntu created because it likes to use extra partitions.

I want to make a new one to experiment with Vista Beta on, but gparted won't let me create more than 4 "primary" partitions. How can I go around this? Thanks!

---

### Post by lamego on 2006-02-01
Recreating/configuring the others as extended ?

---

### Post by Curlydave on 2006-02-01
[QUOTE=lamego]Recreating/configuring the others as extended ?[/QUOTE]

How would I do this? This solution is also proposed by gparted, but without instructions.

Edit: Apparently there already is an extended partition which swap is in. Is there a way to move my FAT partition into the extended one?

---

### Post by Herman on 2006-02-01
Just create a 'logical', and it should automatically appear within an 'extended' partition like one box inside another. :-D (Herman)

---

### Post by Herman on 2006-02-01
> Edit: Apparently there already is an extended partition which swap is in. Is there a way to move my FAT partition into the extended one?
You'll probably need to first move or back up all your data and then delete the data partition if it is 'primary', and create it again as a 'logical' FAT32 partition. Then move your data back into it again afterwards.
This will be okay as long as your two  (or as many as you like) 'logical' partitions are 'contiguous' (placed one after the other on your disk), without any other 'primary' partitions in the middle. :-D (Herman)

---

