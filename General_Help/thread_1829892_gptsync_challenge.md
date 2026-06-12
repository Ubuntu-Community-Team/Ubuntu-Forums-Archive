---
title: "gptsync challenge"
date: 2011-08-20
forum: General Help
---

### Post by Cpierce on 2011-08-20
I have a triple boot with OSx snow leopard, Ubuntu 10.04, and win7. My disk is setup as GPT for OSx. So the partitions I made are 1-boot, 2-OSx, 3-Ubuntu, 4-Win7, and 5-storage. I had to run gptsync to create a hybrid GPT/MBR disk to install windows. Everything works perfectly, except that win7 can't see my fifth storage partition. I tried running "sudo gptsync /dev/sda 5" but it says no sync is needed. OSx and Ubuntu see the storage partition just fine. 

What am I missing ? What gptsync command do I need to run to make the 5th partition visible to win7? 

I love Ubuntu, I believe it is the best OS there is. I find humor in the fact that I am using Ubuntu to fix the other OS's.

---

