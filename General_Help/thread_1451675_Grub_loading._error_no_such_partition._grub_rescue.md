---
title: "Grub loading. error: no such partition. grub rescue&gt; _"
date: 2010-04-10
forum: General Help
---

### Post by dkloeppe on 2010-04-10
I was and idiot and stared messing around gparted before I was ready to partition my hard drive. Consequently I messed up my partitions, and when I restarted my computer a screen comes up that reads:

------------------------------------------------------------------------------------------------------

GRUB loading.
error: no such partition
grub rescue> _

------------------------------------------------------------------------------------------------------

Have I killed my computer or is there some way I can fix it?

---

### Post by nemilar on 2010-04-10
Can you post more details on what exactly you did?

Did you delete your boot partition?

---

### Post by nilesr on 2010-04-10
The same thing happened to me, I resized a partition using gparted live stable and now it says that same thing
/dev/sda3 is extended
/dev/sda5 is linux mint(70.64GiB)
/dev/sda6 is swap(3.88GiB)
Every thing looks OK, set to boot and all that
HELP!!!I need that data!!

---

### Post by nilesr on 2010-04-10
I reinstalled mint on a new partition made in the setup prosses so that they boot side by side then uninstalled the new one I just made, works great.:):):)

---

### Post by dkloeppe on 2010-04-10
> **nemilar said:**
> Can you post more details on what exactly you did?

Did you delete your boot partition?


I think i did delete my boot partition, and I can't figure out how to get into bios mode in order to get it to boot from a cd or external hard drive.  It just shows me that one screen, and none of the commands I've tried so far have worked.  I think I was messing with creating a partition table or something, and then adding a new partition.

---

### Post by dkloeppe on 2010-04-10
Ok, I think i figured it out, i finally got into bios mode and partitioned my hard drive correctly by booting up my gparted live cd, thanks for the help! the links were quite helpful!

---

