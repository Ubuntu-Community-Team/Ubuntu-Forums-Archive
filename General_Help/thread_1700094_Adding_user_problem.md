---
title: "Adding user problem"
date: 2011-03-04
forum: General Help
---

### Post by tailwhipm on 2011-03-04
When i try to add a new user to the home directory wit this  ```
useradd hl2server -d /home/hl2server
```but i get this error ```
useradd: cannot lock /etc/passwd; try again later.

```
any reason why?

---

### Post by turtle153 on 2011-03-04
Are you root? Try```

[FONT=monospace]sudo useradd hl2server -d /home/hl2server

```
[/FONT]

---

### Post by vivek.pandey on 2011-03-04
use 
sudo useradd hl2server -d /home/hl2server

---

### Post by tailwhipm on 2011-03-04
wow that was a stupid mistake of me didnt even think to run it as root. thank you!!

---

