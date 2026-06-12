---
title: "Can't add ppa, module error"
date: 2011-03-30
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2011-03-30
```

maximida@K52JR-X4:~$ sudo apt-add-repository ppa:synapse-core/ppa
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 3, in <module>
    import os
  File "/usr/lib/python2.6/os.py", line 398, in <module>
    import UserDict
  File "/usr/lib/python2.6/UserDict.py", line 82, in <module>
    import _abcoll
  File "/usr/lib/python2.6/_abcoll.py", line 11, in <module>
    from abc import ABCMeta, abstractmethod
ImportError: No module named abc

```

What could I try?

---

