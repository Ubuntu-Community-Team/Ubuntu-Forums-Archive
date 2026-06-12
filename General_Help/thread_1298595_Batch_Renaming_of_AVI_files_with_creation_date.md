---
title: "Batch Renaming of AVI files with creation date"
date: 2009-10-23
forum: General Help
---

### Post by mitsugiri on 2009-10-23
I have a bunch of files imported from my digital camera and they all import as "DSCF****.AVI" for e.g. DSCF0001.AVI.  I would like to rename the files with a batch script to replace the "DSCF****" part with the date from the creation date (e.g. 090924_0001.AVI).  Can this be done?

Thanks a bunch.

---

### Post by Vermind on 2009-10-23
First, check if the creation dates are ok by right-clicking and choosing properties on the files. if they look ok to you, you can do something like this in the terminal, in the folder where the AVIs are:

```
for k in DSCF*.AVI; do 
name=$( ls -l "$k"  | awk '{ gsub("DSCF", "", $NF); 
print $(NF-2)"-"$(NF-1)"_"$NF}' ); 
echo "moving $k to $name"; mv "$k" "$name"; done
```

It should print something like:
moving DSCF0001.AVI to 2009-10-23-09:18_0001.AVI
moving DSCF0002.AVI to 2009-10-23-09:18_0002.AVI
moving DSCF0022.AVI to 2009-10-23-09:18_0022.AVI

The time format will depend on your system settings.

---

### Post by KlinerDraken on 2009-10-23
here is a python script that i hacked together from stuff i found on the net. should do what you need. 
file format is like "10232009_1.avi" after renamed


```

#!/usr/bin/python

import re, os, time, stat
from time import localtime
rxin = ".*avi"
foo = re.compile(rxin)
a = 0
for fname in os.listdir(os.getcwd()):
    allowed_name = re.compile(rxin).match
    if allowed_name(fname):
        a += 1
        c = os.path.splitext(fname)
        file_stats = os.stat(fname)
        file_info = {
           'f_ct': time.strftime("%m%d%Y",time.localtime(file_stats[stat.ST_CTIME]))
        }
        newname = "%(f_ct)s" % file_info
        b = (newname + "_" + str(a) + c[1])
        os.rename(fname, b)
```

---

### Post by mitsugiri on 2009-10-23
Vermind your suggestion seemed to do the trick. Very simple and effective but I can't tell exactly what the script is doing. Specially the second line.  Could you please elaborate?  Also if you could point out a good source where I can learn shell scripting I would much appreciate it.  Kliner I haven't tried your solution yet but I will give it a go later.

Thanks both of you.

---

