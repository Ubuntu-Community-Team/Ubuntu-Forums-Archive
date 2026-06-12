---
title: "'fdisk' not working"
date: 2010-11-10
forum: General Help
---

### Post by c2tarun on 2010-11-10
i tried fdisk -l command on my terminal but it is not giving any output.

here is my /proc/partitions file output

```

$ cat /proc/partitions
major minor  #blocks  name

   8        0  312571224 sda
   8        1   30240768 sda1
   8        2          1 sda2
   8        3  133352448 sda3
   8        4  138796030 sda4
   8        5    8833024 sda5

```

---

### Post by srs5694 on 2010-11-10
You need root access to use fdisk; try "sudo fdisk -l" rather than "fdisk -l".

---

