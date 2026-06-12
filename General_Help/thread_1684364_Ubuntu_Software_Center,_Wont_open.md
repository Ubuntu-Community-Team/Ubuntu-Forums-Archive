---
title: "Ubuntu Software Center, Wont open"
date: 2011-02-09
forum: General Help
---

### Post by Osmium1 on 2011-02-09
Hey, just installed Ubuntu for the first time, but im having trouble getting the Software Center to run.

Ive installed all the updates available.

And im not getting any errors when I run this code.

```
sudo apt-get update
```

When I try to open the Software Center from the Terminal, I get this error.

```
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
IOError: [Errno 5] Input/output error: '/home/osmium/.cache/software-center/software-center.log'
```

---

### Post by [Snc] on 2011-02-09
Can you please post whatever is in
```
/home/osmium/.cache/software-center/software-center.log
```

---

### Post by Osmium1 on 2011-02-10
Wont let me access the log. :confused:
```
bash: /home/osmium/.cache/software-center/software-center.log: Permission denied
```

---

### Post by Perfect Storm on 2011-02-10
```
cat ~/.cache/software-center/software-center.log
```

---

### Post by Osmium1 on 2011-02-10
Thanks for the help but im gona give up on trying to run Ubuntu on my Acer laptop..too many bugs..my laptop fan doesnt even run...probably just going to run windows till i get a new pc.

---

