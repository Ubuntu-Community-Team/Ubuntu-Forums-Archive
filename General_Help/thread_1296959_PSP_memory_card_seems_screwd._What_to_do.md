---
title: "PSP memory card seems screwd. What to do?"
date: 2009-10-21
forum: General Help
---

### Post by macabro22 on 2009-10-21
All my isos and most other files have suddenly disappeared from the memory card. I suspect a files system failure. Is it possible to recover lost files?

How can I run a file system check on my psp?

---

### Post by CyberJack on 2009-10-21
You can run "fsck.vfat" to check for errors.
If your device is /dev/sdb1 you can try the following.
Unmount the device, but leave it connected. Then run
```

sudo fsck.vfat /dev/sdb1

```
This will tell you if there are errors. By my knowledge it does not correct the problems unless you specify the -a option.

I don't know if this works when connecting your psp to your computer.
I always use a memory card reader when dealing with memory cards.

---

### Post by macabro22 on 2009-10-21
```
sudo fsck.vfat -a /dev/sdd1 -a
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
File system has 122433 clusters but only space for 122366 FAT entries.
```

There seems to be a problem but the -a option will not fix it. What to do?

---

