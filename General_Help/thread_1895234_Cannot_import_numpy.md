---
title: "Cannot import numpy"
date: 2011-12-14
forum: General Help
---

### Post by niuri_cigarete on 2011-12-14
Hello everyone,

I've trying to set up a road surface temperature and condition forecast model called Metro here and ran into some problems. 

I had problems installing it but I managed to fix them. But now when I try to do a self test just to see does it work properly, I get this error:

```
$ python metro --selftestTraceback (most recent call last):
  File "metro", line 85, in ?
    import metro_logger
  File "/home/lauryna/Documents/metro/usr/share/metro/metro_logger.py", line 40, in ?
    import metro_config
  File "/home/lauryna/Documents/metro/usr/share/metro/metro_config.py", line 54, in ?
    from toolbox import metro_config_validation
  File "/home/lauryna/Documents/metro/usr/share/metro/toolbox/metro_config_validation.py", line 43, in ?
    import metro_error
  File "/home/lauryna/Documents/metro/usr/share/metro/metro_error.py", line 45, in ?
    from toolbox import metro_util
  File "/home/lauryna/Documents/metro/usr/share/metro/toolbox/metro_util.py", line 71, in ?
    import numpy
ImportError: No module named numpy
```

The problem here is that python-numpy package IS installed but somehow the model cannot import it.

If you need some info about the model, [go here]("http://documentation.wikia.com/wiki/METRo").

Btw, I'm using a Virtual Box and Ubuntu 11.04. Since I'm a total newbie to Linux, please be patient with me :)

---

