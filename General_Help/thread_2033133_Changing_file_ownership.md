---
title: "Changing file ownership"
date: 2012-07-25
forum: General Help
---

### Post by raysa on 2012-07-25
How can I change the ownership of directories and all their files?

After a computer crash I have transferred all my data files (backed up using the 'backintime' application) on to a temporary computer, but they've become root-owned so cannot be written to from their normal apps.

Thanks, Ray

---

### Post by Wirephire on 2012-07-25
```
sudo chown -R $USER /path/to/folder
```This will change the ownership of all files in the selected folder.


*~wph*

---

### Post by Dave_L on 2012-07-25
You probably should change both the user and group:

```
sudo chown -R $USER:$USER /path/to/folder
```

---

### Post by raysa on 2012-07-25
Brilliant - thank you.

---

