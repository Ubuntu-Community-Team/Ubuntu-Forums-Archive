---
title: "Can I safely remove dmraid?"
date: 2011-02-14
forum: General Help
---

### Post by JohnFante on 2011-02-14
Can I safely remove dmraid?

I have a raid0 install of win7 on a jmicron controller (ubuntu is on a SSD on a ich10r controller). The jmicron chip is noted for not working great on Linux when it is running fakeraid. I get a lot of errors when I boot and sometimes the raid0 volume is mounted and sometimes it is not.

I only use the win7 for some gaming etc. and I do not need to be able to mount the drives. 

So can I safely remove dmraid so I do not get any errors on boot etc.?

---

### Post by Jouke74 on 2011-02-14
I strongly suggest you comment the drives from RAID with "# " before the line in Fstab first.

---

### Post by JohnFante on 2011-02-15
They are not present in fstab :-(

Only my linux partitions are.

---

### Post by ronparent on 2011-02-15
If you don't need to access raid0 windows partitions or any interactions with windows data there is no reason to keep dmraid!

---

