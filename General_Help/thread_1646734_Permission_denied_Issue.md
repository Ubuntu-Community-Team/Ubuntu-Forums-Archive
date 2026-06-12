---
title: "Permission denied Issue"
date: 2010-12-16
forum: General Help
---

### Post by anirbanghosh on 2010-12-16
When ever I try to run some executable from Windows drive, terminal says "Permission denied".
I am using Ubuntu 10.10. Facing the same problem when I try to run some program from CodeBlocks or Codelite.

```
anirban@anirban-Studio-1555:~$ cd /media/WORKS
anirban@anirban-Studio-1555:/media/WORKS$ gcc a.c
anirban@anirban-Studio-1555:/media/WORKS$ ./a.out
bash: ./a.out: Permission denied
anirban@anirban-Studio-1555:/media/WORKS$ 

```

---

### Post by karthick87 on 2010-12-16
Try sudo infront of the command,
```

sudo ./a.out
```

---

### Post by anirbanghosh on 2010-12-16
> **karthick87 said:**
> Try sudo infront of the command,
```

sudo ./a.out
```

```
anirban@anirban-Studio-1555:/media/WORKS$ sudo ./a.out
sudo: ./a.out: command not found
```

---

### Post by karthick87 on 2010-12-16
What program you are trying to execute..

---

### Post by santakdalai90 on 2011-02-20
I am also facing the same problem and I got a description regarding the topic that the windows drive is being mounted in "noexec" mode as determined by /etc/fstab. Can anybody post a solution for it, about how to modify fstab file so that the above problem is resolved

---

