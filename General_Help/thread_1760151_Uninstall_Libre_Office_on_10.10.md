---
title: "Uninstall Libre Office on 10.10"
date: 2011-05-16
forum: General Help
---

### Post by oceanfirehawk on 2011-05-16
Hello all,

I like openoffice interface more than libreoffice in ubuntu 10.10. how do i uninstall libreoffice from the terminal? 
Thanks

I was able to remove it from package manager but when I went into add/remove software and tried to install openoffice it gave me this message:

Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

any help?

---

### Post by ajgreeny on 2011-05-16
Did you use the **remove,** or **completely remove** option in synaptic?  Maybe that is the problem, if you did not get rid of the configurations in the filesystem.

---

### Post by kkraju4u on 2012-01-31
use 
sudo apt-get remove libreoffice*.*

enjoy!!

---

### Post by bluexrider on 2012-01-31
```
sudo apt-get update

sudo apt-get remove --purge libreoffice

sudo apt-get clean

sudo apt-get autoremove

sudo apt-get install openoffice 
```

that should do it. if any errors please post back

---

### Post by hpvpp on 2012-04-08
make that

sudo apt-get remove --purge libreoffice*.*

---

### Post by aerotux on 2012-06-06
Also be sure to remove the libre office repositories from your apt sources.

---

