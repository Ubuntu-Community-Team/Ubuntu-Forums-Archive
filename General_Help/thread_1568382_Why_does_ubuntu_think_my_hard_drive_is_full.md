---
title: "Why does ubuntu think my hard drive is full"
date: 2010-09-05
forum: General Help
---

### Post by Evil Wayz on 2010-09-05
I'm getting that stupid  >ICEauthority error.  But df -l shows 93% free, and I've adjusted the reserve to 1%, and I know for a fact that there is 17 gbs of free space.  So I can't get it to update or upgrade even in cli.  Please help because 1) all my porn is on that computer and 2) I'm going to set my computer on fire if it doesn't act right.  Thank you.

---

### Post by no2498 on 2010-09-05
you may need to look using sudo

---

### Post by Evil Wayz on 2010-09-05
> **no2498 said:**
> you may need to look using sudo
Look at what?  THere's 17 gb of space yet, but when i try to upgrade  iget the no space left on device, which means it won't boot. I need to know 1) why the computer thinks this and yes i have used tune2fs to change the reserve from 5 to 1% and 2) how to fix this problem.

---

### Post by Evil Wayz on 2010-09-05
also when i run e2fsck it gives me the mounted system warning, but when I run umount it says /dev/sda isn't mounted. I'm also getting a bad superbloc  error but when i run e2fsck with alternate block it says something about a magic number, and when i use -B it gives me the same bad superblock message. 

and here's the fun part kids, all my shares are perfectly accessible remotely, but i cant log in or get a gdm at the computer.  This is why i hate Ubuntu, because when it breaks, it breaks COMPLETELY.  Only my hatred of Microsoft keeps me using it.

---

