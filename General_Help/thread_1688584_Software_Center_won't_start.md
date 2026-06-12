---
title: "Software Center won't start"
date: 2011-02-15
forum: General Help
---

### Post by CedarPointer on 2011-02-15
I've already tried reinstalling it and all of the Python packages from Synaptic.  (See, I did my homework! :) )
Here's the terminal output I get trying to start it:
```
[my name]@ubuntu:~$ /usr/bin/software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 38, in <module>
    import softwarecenter.log 
  File "/usr/share/software-center/softwarecenter/log.py", line 94, in <module>
    backupCount=5)
  File "/usr/lib/python2.6/logging/handlers.py", line 112, in __init__
    BaseRotatingHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/handlers.py", line 64, in __init__
    logging.FileHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/__init__.py", line 827, in __init__
    StreamHandler.__init__(self, self._open())
  File "/usr/lib/python2.6/logging/__init__.py", line 846, in _open
    stream = open(self.baseFilename, self.mode)
IOError: [Errno 5] Input/output error: '/home/joey/.cache/software-center/software-center.log'

```Any ideas?

---

### Post by TeoBigusGeekus on 2011-02-15
Try renaming the offending file
```
/home/joey/.cache/software-center/software-center.log
```
to
```
/home/joey/.cache/software-center/software-center.log.invalid
```
and try opening software center again.

---

### Post by CedarPointer on 2011-02-15
Works perfectly.  Thank you!!

---

### Post by TeoBigusGeekus on 2011-02-15
Brilliant! You can now delete 
```
/home/joey/.cache/software-center/software-center.log.invalid
```

---

