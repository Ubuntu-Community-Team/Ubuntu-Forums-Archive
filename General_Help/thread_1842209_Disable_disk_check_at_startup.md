---
title: "Disable disk check at startup"
date: 2011-09-10
forum: General Help
---

### Post by hypheni on 2011-09-10
I use ext2 file system for ubuntu 10.04 LTS. and also access this ext2 drive from windows xp by IFS Drives.

Now most of the time I boot to ubuntu I get the annoying disk check which takes a lot time. How can I disable it, I tried by ubuntu disk check disable which is set to 0 for never check but I think this problem is related to accessing the disk from windows and I have installed whole ubuntu system on /dev/sda2 on /.

---

### Post by jv2112 on 2011-09-11
tune2fs -c 0 /dev/drive's you are concerned about.

The 0 will turn it off however it is a good practice to let it check it on occasion to ensure any errors get corrected. I would suggest changing the 0 to a number you don't find annoying. The # represents the # of times mounted between checks so the frequency will be dictated by the # of times you turn the computer on & off.


Hope this helps.

---

### Post by hypheni on 2011-09-12
Earlier I did this but still ubuntu checks for disk errors. I know 0/-1 disable this option but didn't work for me. 

I guess I installed whole ubuntu on a single partition which was mounted on \ and accessing this disk from windows xp for read-write and this causing the problem. Is it so ?

---

### Post by dcstar on 2011-09-12
> **hypheni said:**
> Earlier I did this but still ubuntu checks for disk errors. I know 0/-1 disable this option but didn't work for me. 

I guess I installed whole ubuntu on a single partition and mount it on \ and accessing this disk from windows xp for read-write.

A filesystem marked as dirty will always be checked, if you are mounting this filesystem in another OS and not correctly unmounting it then this can happen.

---

### Post by hypheni on 2011-09-12
I use Ext2IFS for mounting and using ubuntu partition on xp. So anyway to clean unmount of ext2 from xp ?

---

