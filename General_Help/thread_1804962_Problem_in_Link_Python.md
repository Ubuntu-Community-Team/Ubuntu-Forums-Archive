---
title: "Problem in Link Python"
date: 2011-07-15
forum: General Help
---

### Post by qingkunl on 2011-07-15
Hello,

Previously, my python module numpy was installed locally using /usr/**local**/bin/python2.6. And link to this module by setting:
```
#export PYTHONUSERBASE=~/local
#export PYTHONPATH=~/local/lib/python2.6:$PYTHONPATH
```

Then, due to some reason, I re-installed my python to /usr/bin/python2.6. But this time I cannot link to the module numpy with newly installed python. Complaining:
> ImportError: /n/adrian/y/qingkunl/local/lib/python2.6/site-packages/numpy/core/multiarray.so: undefined symbol: PyUnicodeUCS2_AsASCIIString


Does anyone know how to solve this. Do I need to re-install the module?

Thanks,
Qingkun

---

