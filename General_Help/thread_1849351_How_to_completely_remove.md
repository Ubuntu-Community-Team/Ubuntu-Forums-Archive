---
title: "How to completely remove"
date: 2011-09-24
forum: General Help
---

### Post by riff76 on 2011-09-24
hi everyone!

just asking how to completely remove installed apps
(vanish on the entire system) ex: miro tv



TIA!

---

### Post by TeoBigusGeekus on 2011-09-24
Normally, a
```
sudo apt-get purge name-of-app
```
will do the job.
If you installed from source, you navigate into the source folder again and give a
```
sudo make uninstall
```
In both cases, do a
```
find ~/ -iname "*name-of-app*"
```
to find any configuration folders of the uninstalled app in your home partition.
You can then delete them or keep them.

---

### Post by riff76 on 2011-09-24
> **TeoBigusGeekus said:**
> Normally, a
```
sudo apt-get purge name-of-app
```will do the job.
If you installed from source, you navigate into the source folder again and give a
```
sudo make uninstall
```In both cases, do a
```
find ~/ -iname "*name-of-app*"
```to find any configuration folders of the uninstalled app in your home partition.
You can then delete them or keep them.


thaks sir teo now i do hve an idea how to do it.

---

### Post by TeoBigusGeekus on 2011-09-24
You're welcome and don't forget to mark the thread as solved.

---

