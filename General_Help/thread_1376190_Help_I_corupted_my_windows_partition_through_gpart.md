---
title: "Help I corupted my windows partition through gparted"
date: 2010-01-08
forum: General Help
---

### Post by reffu on 2010-01-08
I was resizing my windows partition and accidently turned my computer off. When I went to run a disk check from gparted I get multiple filesystem errors. Chkdsk /r when run from a recovery cd says it can't determine the size of the partition so it can't continue. Is there anyway to get my files off the corrupted partition from within linux. Right now Gparted shows that it has been resized but that it is corrupted and i can't even attempt to mount it. There are only a few files I need to get off the partition but they are really important. Any advice would be greatly appreciated.

Thanks,

reffu

BTW It was also moving the partition to the left 200 mb which is probably the real reason its badly corrupted. It got about 30% of the things moved to the left before it shutdown.

---

### Post by Leppie on 2010-01-08
you could try testdisk:
```
sudo apt-get install testdisk
sudo testdisk
```

---

### Post by reffu on 2010-01-08
Thanks I am running it now I'll let you know how it goes.

---

### Post by reffu on 2010-01-08
Thanks I am copying my important files over now. Next Time I donate money to a project it is definitely going to testdisk.

---

