---
title: "Not able to add new programs"
date: 2010-06-03
forum: General Help
---

### Post by nlindz2065 on 2010-06-03
Hello, I am trying to add a program that will allow me to play wmv files on my computer.  I'm not sure what version of Ubuntu I am using but I keep getting a message that says:
E:dpkg was interrupted, you must manually run'dpkg --configure -a'to correct the problem.
E:_cache->open()failed,please report.
When I try to run this in the terminal I get a message saying I need to be a superuser.  Can anyone help me?

---

### Post by lisati on 2010-06-03
Try:
```
sudo dpkg --configure -a
```

---

