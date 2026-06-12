---
title: "dd filesystem to sdcard with extra space"
date: 2011-07-26
forum: General Help
---

### Post by Oryan02 on 2011-07-26
I'm need to dd a filesystem to a sdcard:
 
dd if=rootfs.ext2 of=/dev/mmcblk0p2
 
works great, but now when I try to add more files to the newly made filesystem I get "No space left on Device". 
 
I df and see that I am only using 1 1-K block out of 118+. I believe I'm using dd wrong (should add some combination of ibs,obs?), could anyone point me in the right direction?

---

