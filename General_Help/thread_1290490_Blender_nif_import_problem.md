---
title: "Blender nif import problem"
date: 2009-10-13
forum: General Help
---

### Post by Liolikas on 2009-10-13
```

$ blender
Compiled with Python version 2.6.2.
Checking for installed Python... got it!
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/home/Lioliks/.blender/scripts/nif_import.py", line 20, in <module>
    from nif_common import NifImportExport
ImportError: No module named nif_common

```
help. ty.

---

### Post by musp on 2010-07-01
Hi,

I just had the same problem but were able to solve it.

if you were trying to install the skripts by the install.sh included it might have happened that the nif_common.py could not be written into the bpymodules-folder because you did not have permission to write into it.

I simply solved it by executing the skript in bash as superuser:
> 
sudo sh install.sh


Perhaps someone googling for the same issue may find this useful.

---

