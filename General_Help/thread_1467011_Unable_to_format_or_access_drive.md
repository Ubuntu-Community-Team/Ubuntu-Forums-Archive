---
title: "Unable to format or access drive"
date: 2010-04-30
forum: General Help
---

### Post by cyberjar09 on 2010-04-30
I want to format a partition on my computer but i keep getting errors like this 

"Error creating file system: helper exited with exit code 1: helper failed with:
Total number of sectors (1318342094) not a multiple of sectors per track (63)!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test"

I cant even access the drive ... whats the matter? it is the same physical drive as the one on which my linux os is installed... but a different partition.

Thanks.

---

### Post by joelorenzo on 2011-06-29
I got that same error, only I am trying to reformat and external hard drive. I can't figure it out :/

---

### Post by varunendra on 2011-06-30
Please mention which software tool you are using to format the partition.

Make sure it is unmounted, then try fsck on that partition to fix possible errors. I'd recommend gparted for performing partition management tasks.

---

### Post by cyberjar09 on 2011-06-30
> **joelorenzo said:**
> I got that same error, only I am trying to reformat and external hard drive. I can't figure it out :/

yes my problem has long been resolved. I can't seem to recall the exact nature of the problem but try what varunendra recommends and post back if still unresolved.

---

