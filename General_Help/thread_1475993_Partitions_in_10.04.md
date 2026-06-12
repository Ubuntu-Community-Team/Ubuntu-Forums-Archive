---
title: "Partitions in 10.04"
date: 2010-05-07
forum: General Help
---

### Post by iblazev on 2010-05-07
Hello!
I have 6 partitions on 2 disk and new install of Ubuntu 10.04 has found them all correctly. 
Now, when I go to *Places* I can see them all there but in *fstab* there are only */, swap* and *home*. 
From where do those 3 that aren't in *fstab* come to *Places* menu? :-k

---

### Post by dino99 on 2010-05-07
can install mountmanager to tweak your devices and partitions as you need

---

### Post by iblazev on 2010-05-07
Thanx but I was curious to learn something new :) Where are config files for those partitions or something like that.

---

### Post by lmarmisa on 2010-05-07
The installation procedure only adds your two partions (**/ **and **swap**; **/boot** or other system partitions are also added if needed) to the /etc/fstab file for auto-mounting at startup.  You can add more partitions manually, of course.

You can see the partitions detected by the system typing the following command:

> 
sudo fdisk -l
Best regards,

Luis

---

### Post by WorMzy on 2010-05-07
If the partition is not in fstab, then Ubuntu will automatically decide what arguments to mount the partition with, and assign it a location by using it's label, or UUID if it doesn't have a label. After it has mounted the partition, it creates a line in /etc/mtab which shows you what arguments it has used to mount. If you don't agree with the arguments it has used, you can then add a line to fstab using the mtab entry as a template, umount the drive, and then re-mount it. 

Quenches your thirst for knowledge. :)

---

### Post by iblazev on 2010-05-08
Thanx all :) Didn't know about that *mtab* part..

---

