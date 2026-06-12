---
title: "Calibre failed to convert epub to mobi"
date: 2011-02-06
forum: General Help
---

### Post by kievking on 2011-02-06
I received this message in the terminal window when I tried to convert an ebook to the mobi format. Any suggestions?

ICE default IO error handler doing an exit(), pid = 1912, errno = 32

Exception in thread Thread-3 (most likely raised during interpreter shutdown):
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
  File "/usr/lib/calibre/calibre/utils/ipc/server.py", line 167, in run
  File "/usr/lib/python2.6/Queue.py", line 177, in get
  File "/usr/lib/python2.6/threading.py", line 254, in wait
<type 'exceptions.TypeError'>: 'NoneType' object is not callable
Exception in thread Thread-8 (most likely raised during interpreter shutdown):
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
  File "/usr/lib/calibre/calibre/utils/ipc/server.py", line 167, in run
  File "/usr/lib/python2.6/Queue.py", line 177, in get
  File "/usr/lib/python2.6/threading.py", line 254, in wait
<type 'exceptions.TypeError'>: 'NoneType' object is not callable
Exception in thread Thread-4 (most likely raised during interpreter shutdown):
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
  File "/usr/lib/calibre/calibre/gui2/device.py", line 445, in run
  File "/usr/lib/python2.6/threading.py", line 117, in acquire
<type 'exceptions.TypeError'>: 'NoneType' object is not callable
Segmentation fault

---

### Post by kievking on 2011-02-06
Problem solved

[http://www.linuxforums.org/forum/suse-linux/95858-ice-default-io-error-handler.html](http://www.linuxforums.org/forum/suse-linux/95858-ice-default-io-error-handler.html)

---

