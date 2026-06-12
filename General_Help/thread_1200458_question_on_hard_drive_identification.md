---
title: "question on hard drive identification"
date: 2009-06-30
forum: General Help
---

### Post by mxu on 2009-06-30
hi, guys,

I have a small question on how to identify failure hard. I have build an raid 5 array of several hard drives of the same model and same capacity. If one of them fails, then I can know from cat /proc/mdstat that a disk /dev/sdX fails, for some X. However, my question is how to know which physical drive does this /dev/sdX correspond? For example, is there any way to get the serial number of the hard drive of /dev/sdX, so that I can tell from looking at the lable of the drive?

Thank you very much,
mxu

---

### Post by plucky on 2009-06-30
What does ```
sudo lshw -C disk
``` from a terminal window show you?

Good Luck

---

### Post by mxu on 2009-06-30
Yes, I got the serial number from the lshw. Thank you very much plucky!

---

