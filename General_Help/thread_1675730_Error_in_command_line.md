---
title: "Error in command line"
date: 2011-01-26
forum: General Help
---

### Post by ritesh2190 on 2011-01-26
I am new to ubuntu nd whenever i try to install a package using the terminal i get this error
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  E: _cache->open() failed, please report.
pls help

---

### Post by wojox on 2011-01-26
What happens when you run this command:

```
sudo dpkg --configure -a
```

---

### Post by lisati on 2011-01-26
> **ritesh2190 said:**
> I am new to ubuntu nd whenever i try to install a package using the terminal i get this error
E: dpkg was interrupted, [COLOR="Red"]you must manually run 'sudo dpkg --configure -a' to correct the problem[/COLOR].  E: _cache->open() failed, please report.
pls help

The highlighted bit is what you need to do. :)

---

