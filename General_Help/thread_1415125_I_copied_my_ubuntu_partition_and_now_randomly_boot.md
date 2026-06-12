---
title: "I copied my ubuntu partition and now randomly boots into either."
date: 2010-02-24
forum: General Help
---

### Post by salviablue on 2010-02-24
Hello peeps,
I copied my main ubuntu studio partition from one physical hd to another, both hd's being in the one machine, using gparted. This is because I suspect the hd to be failing. 
Now when I boot up, it sometimes boots into the original part and sometimes into the copied one.
I would like the copied one to be the running part until I replace the failing drive. Then copy the part onto the new drive and have it as the "live" part.



ubuntu studio 8.04 (2.6.24-27-rt)

---

### Post by sisco311 on 2010-02-25
Change the UUID of the new partition:
```
sudo tune2fs -U random /dev/sdXY
```
then edit the /boot/grub/menu.lst & /etc/fstab files and replace the the old UUID with the new one.

---

