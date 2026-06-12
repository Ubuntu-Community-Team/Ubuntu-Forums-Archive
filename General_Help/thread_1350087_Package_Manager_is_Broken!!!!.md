---
title: "Package Manager is Broken!!!!"
date: 2009-12-08
forum: General Help
---

### Post by shifterdriver13 on 2009-12-08
Hey all, my package manager won't let me install anything, synaptics won't even come up, whenever I try to open it it comes up with:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report. 

and being a total noob I have no idea what to do, I just want to be able to install applications, so any help is much appreciated.
             
         Thanks in advance

---

### Post by shifterdriver13 on 2009-12-08
oh forgot to mention I'm running xubuntu 8.04 LTS

---

### Post by lisati on 2009-12-08
> **shifterdriver13 said:**
> Hey all, my package manager won't let me install anything, synaptics won't even come up, whenever I try to open it it comes up with:

E: dpkg was interrupted, you must manually run '[COLOR="Red"]dpkg --configure -a[/COLOR]' to correct the problem.
E: _cache->open() failed, please report. 

and being a total noob I have no idea what to do, I just want to be able to install applications, so any help is much appreciated.
             
         Thanks in advance


Go to Applications->Accessories->Terminal and put in ```
sudo dpkg --configure -a
```
It will ask for you password, which will not show as you type.

---

### Post by shifterdriver13 on 2009-12-09
It worked, thank you!!!

---

### Post by lisati on 2009-12-09
> **shifterdriver13 said:**
> It worked, thank you!!!

You're welcome.

---

