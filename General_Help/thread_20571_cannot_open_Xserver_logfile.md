---
title: "cannot open Xserver logfile"
date: 2005-03-17
forum: General Help
---

### Post by largo on 2005-03-17
Hi there... Xfree was runnig fine, but suddenly yesterday after a restart, the system is unable to open a log file

Xserver output:
```
Fatal server error:
Cannot open log file "/var/log/XFree86.0.log"

``` 

when I go into this directory, there is apparently no file with that name, but I cannot create one either. it gives me a permission denied... I also tried to reconfigure the Xserver.. without sucess

---

### Post by alastair on 2005-03-17
Well, a :

sudo touch /var/log/ttt

should work. Do you have a disk space issue?

df

---

