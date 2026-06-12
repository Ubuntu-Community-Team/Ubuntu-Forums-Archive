---
title: "How to Create an smb share pannel launcher?"
date: 2011-05-05
forum: General Help
---

### Post by jfed on 2011-05-05
Hello. I wasn't sure if I should post this in the Network thread, it didn't seem like it, as I presume this is a fairly simple thing to do.

My brother runs storage server over our LAN, I connect to it via smb. (I'm not sure if it's called Samba or just pronounced that way)

Rather than hitting ctrl+l in a file browser window, and typing smb://000.000.0.000/drivename each time, I'd like to know how I can add a launcher to the gnome panel which will do that for me

I know this is possible, because I have done it before, I just forget how. I was going to try creating a launcher application in terminal, but I'm not sure what code to use.

Any input is appreciated, thanks in advance!

---

### Post by Morbius1 on 2011-05-05
```
nautilus smb://000.000.000.000/drive-name
```Is the command you use to in your launcher.

EDIT: Right click the panel > Add to Panel > Custom Application Launcher ............

---

### Post by jfed on 2011-05-05
> **Morbius1 said:**
> ```
nautilus smb://000.000.000.000/drive-name
```Is the command you use to in your launcher.

EDIT: Right click the panel > Add to Panel > Custom Application Launcher ............

Thanks! Works like a charm.

---

