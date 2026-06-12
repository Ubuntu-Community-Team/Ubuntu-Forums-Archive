---
title: "Partition Gone, Ubuntu in Denial"
date: 2010-09-30
forum: General Help
---

### Post by mk_kano on 2010-09-30
Hi all, I installed Windows 7 after Ubuntu, and got everything working fine except that I deleted a partition Ubuntu was using for media and assigned it to my Windows installation. Now when Ubuntu boots it can't find the partition and keeps letting me know this. How can I convince Ubuntu that it really doesn't exist and it doesn't need to mount it any longer?

Using Ubuntu 10.04

Thanks in advance for your wizardry.

---

### Post by andrewthomas on 2010-10-01
Enter in the terminal
```
 
gksudo gedit /etc/fstab

```
Then remove the line that contains the reference to the deleted partition
 
or post the output of ```
cat /etc/fstab
``` and I will tell you what to delete

---

### Post by mk_kano on 2010-10-01
Thanks! Worked great.

---

