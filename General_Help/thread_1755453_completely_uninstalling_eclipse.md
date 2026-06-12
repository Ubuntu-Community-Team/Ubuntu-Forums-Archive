---
title: "completely uninstalling eclipse"
date: 2011-05-11
forum: General Help
---

### Post by nethero on 2011-05-11
I installed eclipse throught synaptic and now I want to get rid of it.  However, when I installed eclipse it also installed a lot of other files.  I don't remember the names of these files but I'd like to remove them also.  How can I find the names of these files so I can remove them?

---

### Post by TeoBigusGeekus on 2011-05-11
```
sudo apt-get purge eclipse
```
will completely remove eclipse. If there are left over files installed as dependencies for eclipse, you can uninstall them with
```
sudo apt-get autoremove
```

---

### Post by nethero on 2011-05-11
Worked perfectly.  Thanks!

---

### Post by mustang on 2011-07-23
> **TeoBigusGeekus said:**
> ```
sudo apt-get purge eclipse
```
will completely remove eclipse. If there are left over files installed as dependencies for eclipse, you can uninstall them with
```
sudo apt-get autoremove
```

Thank you sir

---

### Post by TeoBigusGeekus on 2011-07-23
You're welcome!

---

