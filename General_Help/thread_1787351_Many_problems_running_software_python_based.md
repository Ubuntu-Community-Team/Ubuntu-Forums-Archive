---
title: "Many problems running software python based"
date: 2011-06-21
forum: General Help
---

### Post by karimone on 2011-06-21
Hi all, I just installed Ubuntu 10.4.2 and I got some strange problems running python software. Here the example:

Running terminator
```

karim@alpha-ubuntu:~$ terminator 
ConfigBase::load: Unable to open /home/karim/.config/terminator/config ([Errno 2] Nessun file o directory: '/home/karim/.config/terminator/config')
Segmentation fault
karim@alpha-ubuntu:~$ 

```

Running ubuntu-tweak:
```

karim@alpha-ubuntu:~$ ubuntu-tweak 
Traceback (most recent call last):
  File "/usr/bin/ubuntu-tweak", line 34, in <module>
    from ubuntutweak.common.consts import DATA_DIR, IS_INSTALLED, VERSION
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/common/consts.py", line 57, in <module>
    if not pynotify.init('ubuntu-tweak'):
AttributeError: 'module' object has no attribute 'init'
karim@alpha-ubuntu:~$ 

```

I tried to force the reinstall of many python packages, but I guess is a problem with path or something like that. Any suggestion?

Thanks!

---

