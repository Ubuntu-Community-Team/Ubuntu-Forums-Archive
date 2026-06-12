---
title: "Name of the current partition or hard drive"
date: 2010-08-24
forum: General Help
---

### Post by Zeeyad on 2010-08-24
How can I get the name of my current hard drive (the hard drive that I'm using)?

Actually I know this command sudo fdisk -l , but this command gives you all the partitions what I want to know is if there is any way in which I can get the name of the hard drive or partition that I am using! For example, if I'm working on dev/sda6, I want a command or a file that can give me this name dev/sda6

Thx for ur help.

---

### Post by P1ta on 2010-08-24
use ntfslabel for ntfs partisions and e2label for ext2 or ext3 partitions :

```
ntfslabel /dev/sdc1
HDD500
```

---

### Post by srs5694 on 2010-08-24
```

df -h ./

```

---

### Post by Zeeyad on 2010-08-25
Thx a lot srs5694.

---

