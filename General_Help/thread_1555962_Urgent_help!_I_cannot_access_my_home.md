---
title: "Urgent help! I cannot access my /home/"
date: 2010-08-18
forum: General Help
---

### Post by Alan502 on 2010-08-18
Hi! I got a big problem, i cannot access the partition where my /home is supposed to mount but from a live cd. I didn't do anything unusual that could have caused it, the last thing i did was running the package update. I've tried the recovery console but when i try to mount the partition it says it is "already mounted or /home (or whatever directory i try to mount it to) is busy"

I am now on a live cd, where, fortunately, i can view my files on the parititon. However i noticed that there are two weird files there:  al?.s?id?.pub  al?.s?id?.pub.pub

Please help! tell me is something isn't clear.

---

### Post by Alan502 on 2010-08-18
Ok, i'll put it this way

I cannot mount the partition where i have my /home in any  directory, i can only view it from a live cd. When i try to mount the  parition it says that it "is already mounted or <directory> is  busy." However, when i run umount /dev/sdb7 (which is the partition with  my home directory) it says /dev/sdb7 is not mounted. What could be the  problem?, any help will be appreciated!

---

### Post by Alan502 on 2010-08-18
Okay so if it¡s useful for anybody else, I edited /etc/fstab and changed every partition's "pass" to 2 except /, which i left with 1, and swap & proc, which i left with 0. I don't know how this could have helped but it worked! XD

---

