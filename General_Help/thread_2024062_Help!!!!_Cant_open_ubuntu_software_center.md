---
title: "Help!!!! Cant open ubuntu software center"
date: 2012-07-13
forum: General Help
---

### Post by n123q45 on 2012-07-13
My software center wont open anymore. it just flashes like its going 2 open and then disapears without doing anything. What do i do?

---

### Post by n123q45 on 2012-07-13
now it will show up for a second and disappear. and im not exaggerating

---

### Post by plucky on 2012-07-13
> **n123q45 said:**
> My software center wont open anymore. it just flashes like its going 2 open and then disapears without doing anything. What do i do?

Open a terminal and type in the command ```
software-center
``` and post back the output.

Good Luck

---

### Post by n123q45 on 2012-07-13
```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 40, in <module>
    import softwarecenter.log
  File "/usr/share/software-center/softwarecenter/log.py", line 121, in <module>
    logfile_path, maxBytes=100 * 1000, backupCount=5)
  File "/usr/lib/python2.7/logging/handlers.py", line 118, in __init__
    BaseRotatingHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.7/logging/handlers.py", line 65, in __init__
    logging.FileHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.7/logging/__init__.py", line 897, in __init__
    StreamHandler.__init__(self, self._open())
  File "/usr/lib/python2.7/logging/__init__.py", line 916, in _open
    stream = open(self.baseFilename, self.mode)
IOError: [Errno 5] Input/output error: '/home/nick/.cache/software-center/software-center.log'
```

---

### Post by cortman on 2012-07-13
Try running

```
mv ~/.cache/software-center/software-center.log usc.log.old
```

Then open the software center.

---

### Post by n123q45 on 2012-07-13
it works thx

---

### Post by cortman on 2012-07-13
> **n123q45 said:**
> it works thx

Great- please mark the thread [SOLVED] using the thread tools in the upper right.
Good luck!

---

