---
title: "xfce uninstall"
date: 2005-03-09
forum: General Help
---

### Post by Kimm on 2005-03-09
ok, I installed XFCE today, just to have a look at it, to see what it was.
I used the graphical installer. The installation didnt exactly work perfectly, it failed to compile some parts of it. I can still run it, but some parts wount work. I dont realy think its anything for me anyway.

no... I dont know how to uninstall it, can anyone tell me how I should do that?

---

### Post by DJ_Max on 2005-03-09
If you installed via synaptic of apt-get/
```
sudo apt-get remove <PACKAGENAME>
```
Of course, replace <PACKAGENAME> with the xfce package name.

---

### Post by Kimm on 2005-03-09
I said I used the graphical installer :P not a .deb package...
but I supose I could download the source run configure again and then run make uninstall... I think that should work...

---

### Post by evil_cat on 2007-12-23
Please try

apt-get autoremove xfce4

Works out great

---

