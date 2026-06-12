---
title: "EXt4 in 8.04 Hardy"
date: 2010-09-19
forum: General Help
---

### Post by kwill on 2010-09-19
On a multi boot computer I have 8,04LTS install and have just installed 10.04. both boot but the Hardy cannot read the Lucid ext4 filesystem.

Is there any way to read EXT4 from 8.04LTS?

---

### Post by afrowildo on 2010-09-20
You would have to manually mount the ext4 partition and specify it as an ext3 partition. Ext3 is however only partially forward compatible with ext4, due to the use of *extents* in ext4, which is a major new feature and changes the way in which date is stored on the drive on an ext4 filesystem. If this feature is enabled (and I can't see it not being so unless you installed 10.04 on a preformated ext4 filesystem with some eccentric options), then you're fresh out of luck I'm afraid.

---

### Post by rusty149 on 2010-10-21
Here are instructions to enable ext4 in hardy 8.04. 

[http://ubuntuforums.org/showthread.php?t=1313675&highlight=hardy+ext4]("http://ubuntuforums.org/showthread.php?t=1313675&highlight=hardy+ext4")

---

### Post by kwill on 2010-10-21
Thanks Rusty149,

I will try to compile new kernel.  Tried once before but ran out of time to answer all the questions. Any quick way to compile kernel?

---

### Post by rusty149 on 2010-10-23
That is the quick way. Just paste the code into a terminal and reboot. 
No compiling needed just installing.

---

