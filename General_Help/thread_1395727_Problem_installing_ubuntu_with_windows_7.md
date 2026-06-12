---
title: "Problem installing ubuntu with windows 7"
date: 2010-02-01
forum: General Help
---

### Post by aviramof on 2010-02-01
i have tried to install ubuntu along side with windows 7 when i did the windows installion it 
worked well when i did the full installtion it didn't and also it didn't recognize the partition i
wanted to install ubuntu there this partition is empty but ubuntu installion did not recognize any empty partition to choose from and i don't understand why so when can we expect a new ubuntu version that would support windows 7 better?

thanks in advance.

---

### Post by hero1900 on 2010-02-01
the free partition you have is primary or extended??
if it is extended you cant put ubuntu on it try to make a free primary partition and then install ubuntu on it

---

### Post by aviramof on 2010-02-01
i never use extended partitions but i have to say i really don't understand the options of choosing partition in this os there is install along side there is delete and use all partition or something i'm translating from hebrew and some other options and i don't 
know what to choose i don't want to choose anything that might erase my windows 7 by mistake also i took that empty partition i said earlier and deleted it so i now have 
empty space that i can recognize but i don't know which option to choose in order to 
install in this empty space and to create a dual boot with windows 7.

---

### Post by hero1900 on 2010-02-01
then do manual partition
and then chose your empty partition and delete it and then right click on the free space and then click add then you will see type of file system already ext4 dont touch then chose mount point as / and before you close reduce the space for this partition since you need to give space for swap partition
(for ubuntu you need to define swap area in windows it is automatic) so if you got 40gb free space make 36 as ext4 and mount point as / and then 4 gb as swap
hope it help you

---

### Post by aviramof on 2010-02-01
what i did in the end is this i deleted this partition then choose use the biggest amount of free space which is this partition and the os installer installed ubuntu and created a second partition for the swap file but what he didn't do is to create a dual boot screen and that is my problem now how can i do this manually?

---

### Post by aviramof on 2010-02-01
ok thanks for the help but it doesn't work i can't get ubuntu to create a dual boot with windows 7 or enter ubuntu in any other way and i'm not going to format my win 7 or anything like this so thanks for all the help but i would wait for the next ubuntu version
before i try it again.

and again thanks for all the help.

---

