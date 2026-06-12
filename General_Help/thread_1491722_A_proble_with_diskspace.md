---
title: "A proble with diskspace"
date: 2010-05-23
forum: General Help
---

### Post by ledangkhoalt on 2010-05-23
Hi everybody, i'm  from Vietnam. I have a prolem.

I have a computer, it's running with linux. the mount point /home is in one patition.
After a long time , it hasn't enought free space yet. Hown can we append more disk space on /home with another harddisk.

Thank you.

---

### Post by jbrown96 on 2010-05-24
You will need to setup a LVM. There are a few steps to it, but the first thing is that the new hard drive will have to be at least the same size as your current /home. 

After your new hard drive is connected, then please post the output of the following commands. ```
df -h && sudo fdisk -l
``` and I will help you create the LVM.

---

