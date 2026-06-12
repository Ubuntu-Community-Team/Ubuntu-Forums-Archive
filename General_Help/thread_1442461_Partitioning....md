---
title: "Partitioning..."
date: 2010-03-30
forum: General Help
---

### Post by 664748 on 2010-03-30
Hi,
 
Originally ive got windows xp pro on my pc, but since it crushed down i need to format it again, ive tried using ubuntu 9.10, the platform is so good that i dont want to go back to windows anymore:p but since iam new at this spectacular os i dont know how to partition my disk. can anyone help me with it?

---

### Post by zvacet on 2010-03-30
If you have some valuable data/files back them up.After that boot Ubuntu live CD and during installation you will get to the partitioning section.Select manual way and 

1. root 10GB      ext4         mountpoint  /
2.swap 2GB      
3.home rest of free space  ext 4    mountpoint /home

---

### Post by 664748 on 2010-03-30
just to ask you, if i didnt backed up my files, after partitioning the disk will i lose those files?
 
how can i backup my files on ubuntu anyway?
 
and after partitioning my disk can i install another os on that new partitioned space?

---

### Post by zvacet on 2010-03-30
Put you data on CD,USB,external HD...
Yes you can install other OS after installing Ubuntu but you have to leave unallocated space for it.You will also need to repartition grub after that.See [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by 664748 on 2010-03-30
alright got it. i'll try that. thank you so much for you advice!:)

---

