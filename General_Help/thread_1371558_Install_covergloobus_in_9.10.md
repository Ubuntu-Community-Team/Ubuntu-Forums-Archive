---
title: "Install covergloobus in 9.10"
date: 2010-01-03
forum: General Help
---

### Post by bluestar14 on 2010-01-03
i am trying to install covergloobus, but whenever i try to run config-covergloobus.py file it gives following error:
```
mac4lin@STUDYROOML:~/covergloobus/src$ python covergloobus-config.py
Traceback (most recent call last):
  File "covergloobus-config.py", line 33, in <module>
    import gtk
ImportError: No module named gtk
```                 :confused:

---

### Post by czd on 2010-02-06
Hi,

Try to install python gtk libraries

```

sudo apt-get install python-gtk2

```

---

