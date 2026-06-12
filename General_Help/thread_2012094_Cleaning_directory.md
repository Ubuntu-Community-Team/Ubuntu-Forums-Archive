---
title: "Cleaning directory"
date: 2012-06-28
forum: General Help
---

### Post by klobasmaster on 2012-06-28
I have a folder full of JPGs and I need to remove all the ones smaller than 1 MB. The folder is so big that Nautilus still didnt load it after an hour. Thanks for any help

---

### Post by codemaniac on 2012-06-28
> **klobasmaster said:**
> I have a folder full of JPGs and I need to remove all the ones smaller than 1 MB. The folder is so big that Nautilus still didnt load it after an hour. Thanks for any help

Hello klobasmaster ,

Welcome to the UbuntuForums .

You can use find command in order to look for the files lees than 1MB of size and remove .

Open up a terminal by pressing alt+ctrl+T and issue the following command .
Fire the below command with care .

```
find . -size 1M | xargs rm -f
```

EDIT:
Before issuing the above command , please list the files and be sure you want to remove them .
```
find . -size 1M | xargs ls -l
```

---

### Post by klobasmaster on 2012-06-28
Thanks for the fast help, codemaniac!

---

