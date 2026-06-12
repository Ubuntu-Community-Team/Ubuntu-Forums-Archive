---
title: "disk questions"
date: 2006-03-22
forum: General Help
---

### Post by thunderfox933 on 2006-03-22
hi

i am wonder about disk 

1. is there a way i can check the disk 4 errors

---

### Post by terranz on 2006-03-22
close all your apps and beboot the computer without stutting down by pressing the reset button or switching off.

There is probably a better way but that works for me.

---

### Post by az on 2006-03-22
[QUOTE=thunderfox933]hi

i am wonder about disk 

1. is there a way i can check the disk 4 errors[/QUOTE]

badblocks /dev/hda1 (where hda1 is the correct partition.  Type "mount" to see what your / partition is on.)

---

