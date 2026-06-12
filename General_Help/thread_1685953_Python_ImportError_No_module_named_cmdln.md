---
title: "Python ImportError: No module named cmdln"
date: 2011-02-11
forum: General Help
---

### Post by capt-tuttle on 2011-02-11
Its been a long day
Loading Ubuntu on new office computer and overcoming the black screen and several small issues but this one is winning
Running a known good python script, from an older machine, and I vaguely remember this issues watching the last time it was installed but can't remember enough
The error is:
ImportError: No module named cmdln
I am guessing its a mater of pointing to the right directory/library but since I am a python user but not programmer I sure could use some help

Thanks
CT

---

### Post by DaithiF on 2011-02-11
i don't think cmdln is packaged for ubuntu.  You can install it with easy_install:
```
sudo apt-get install python-setuptools
sudo easy_install cmdln

```

---

