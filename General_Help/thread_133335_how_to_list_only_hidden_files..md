---
title: "how to list only hidden files."
date: 2006-02-20
forum: General Help
---

### Post by jnk on 2006-02-20
hi....

how do I use the ls command to ONLY list hidden files.?
only files and not directorys...

---

### Post by Lux Perpetua on 2006-02-20
Try ```
ls -al | egrep -e "^-.*[[:space:]]\."
``` (Displays all files beginning with a period, but not directories or links)

edit: If you want *everything* but directories,
```
ls -al | egrep -e "^[^d].*[[:space:]]\."
```

---

### Post by jnk on 2006-02-20
thanx man....!!!
realy fast respond... you saved my day.!!!!

---

### Post by linuxusr50 on 2006-02-20
I think this will do what you are looking for also.


ls -ap | grep -v /

---

### Post by Lux Perpetua on 2006-02-20
[QUOTE=linuxusr50]I think this will do what you are looking for also.


ls -ap | grep -v /[/QUOTE]
Good call on the ls -ap. In order to display only hidden files (files beginning with a period), you could use grep "^\..*[^/]$".

---

