---
title: "Unmounting ext4 with full data journaling"
date: 2011-01-06
forum: General Help
---

### Post by Sworddragon on 2011-01-06
If I try to unmount my hard disk drive I get the message that the device is busy. "lsof | grep sda1" shows me:

```
jbd2/sda1  309        root  cwd       DIR                8,1     4096          2 /
jbd2/sda1  309        root  rtd       DIR                8,1     4096          2 /
jbd2/sda1  309        root  txt   unknown                                        /proc/309/exe
```


I figured out with iotop that on every unmount the journal saves data on the disk. But in this case it's impossible to unmount my drive. Has anybody an idea how to successfull unmount my hard disk drive?

---

