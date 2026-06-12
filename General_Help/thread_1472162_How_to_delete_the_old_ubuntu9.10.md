---
title: "How to delete the old ubuntu9.10 ?"
date: 2010-05-04
forum: General Help
---

### Post by ibrahim.k on 2010-05-04
Hi,

I have installed 10.04 and now I have both of 
ubuntu 9.10 and ubuntu 10.04 installed on the same laptopt.


how can I completely remove the older version of ubuntu 9.10

thnx

---

### Post by dino99 on 2010-05-04
maybe its not a good idea to remove 9.10 now, better to wait a couple weeks to be sure there is no issue with 10.04 on your system.

if lucid cant boot, karmic is still there, think about that.

but if you want to definitly remove it, simply reformat its partition with gparted (into repo) or partedmagic. Then into console:

sudo grub-mkconfig && update-grub

---

