---
title: "Mixing Drives"
date: 2010-01-25
forum: General Help
---

### Post by rockom on 2010-01-25
Hello,

I've edited the kernel line in my grub configuration to add elevator=noop for used with an SSD drive.  That's working fine but, I want to add a platter drive for data and would like to use the standard IO scheduler.  Editing the grub config makes all drives noop.

I can manually setup the platter for another scheduler by echo'ing to '*/sys/block/sdb/queue/scheduler'* but I'd have to do that every time I boot (right?).

How can I setup the platter with a different scheduler?  I want to set it and forget it.

Thanks
-Rocko

---

### Post by t4thfavor on 2010-01-26
Can't you set those options in the fstab file, and leave the kernel line alone? I believe that you can specify that for the / (root), and a separate option for each other drive that is mounted.

---

### Post by rockom on 2010-01-27
> **t4thfavor said:**
> Can't you set those options in the fstab file, and leave the kernel line alone? I believe that you can specify that for the / (root), and a separate option for each other drive that is mounted.

That may be the case.  I have not found any information on how to do so in the fstab file. 

-Rocko

---

