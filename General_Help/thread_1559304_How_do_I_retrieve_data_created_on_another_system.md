---
title: "How do I retrieve data created on another system"
date: 2010-08-23
forum: General Help
---

### Post by old_dog on 2010-08-23
My son's laptop with Ubuntu on went belly up, so before we dumped it I salvaged the hard disk.....now some weeks later he remembers there is some things he wants on the disk. 
Luckily I had done nothing with it ....have just connected the disk to my system I can see everything above(should that be below) home but not anything in his account. 
Any bright ideas for getting at his data is there a way of mass changing permissions  or whatever?
Cheers

---

### Post by anirudhtomer on 2010-08-23
sudo  cp -R  /home/*   /destination/

---

### Post by arpanaut on 2010-08-23
Possibly he created a separate /home partition on the drive?
If so all his data would be on that partition...

Try exploring other partitions on the drive the data may be there.

---

### Post by anirudhtomer on 2010-08-23
if ur /home is on some other partition then

sudo mount /dev/sdax /home    
(x can be any number 1,2 or watever on ur system..check that thing first)

& then
sudo  cp -R  /home/*   /destination/ 	

this way u can copy the data.

---

