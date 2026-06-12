---
title: "Disk Space"
date: 2010-05-31
forum: General Help
---

### Post by blagosphere on 2010-05-31
I used WUBI to install a 17gb ubuntu. I have updated to lucid and am doing great! I have looked for ways to free up disk space. I have done sudo apt-get [clean, autoremove, ect..] and used localepurge as well as removed orphaned packages and residual install files. The only problem is that there are still residual files in my home like [.opera] and [.gimp] that i have removed before!. Is there any way to easily remove these and possibly other files that i dont need?

---

### Post by arrange on 2010-05-31
You can use *bleachbit* - [http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)
But your best bet is to find the big files and remove them (if not needed) :)
```
find ~ -type f -size +100M
```

---

### Post by blagosphere on 2010-05-31
Thanks! bleachbit removed almost 2GB of stuff!

---

