---
title: "CUPS problem after upgrade to 10.10"
date: 2010-10-23
forum: General Help
---

### Post by tOMky on 2010-10-23
Hi,
I recently upgraded from 10.04 server to 10.10 and today noticed that my printer doesn't work. I uninstalled cups and its friends and tried to install again. But it cannot be done because of this:
```
The following packages have unmet dependencies:
 cups : Depends: cups-ppdc but it is not installable
```
Please help me to install CUPS.[LIST=1]
[/LIST]

---

### Post by acedillo on 2010-10-29
I got the same error and I cannot print now

---

### Post by Hippytaff on 2010-10-29
Just on the off-chance, have you tried
```

sudo apt-get install cups-ppdc

```

---

