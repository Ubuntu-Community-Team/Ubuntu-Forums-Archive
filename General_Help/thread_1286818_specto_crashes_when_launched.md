---
title: "specto crashes when launched"
date: 2009-10-09
forum: General Help
---

### Post by chriskin on 2009-10-09
i got specto from ubuntu tweak
it installed finely, i started it and tried to add a feed - it just wouldn't work
so i removed it and i installed it again - now it just won't start any more

when i run it from terminal i get this

```
/usr/lib/python2.6/dist-packages/spectlib/notifier.py:294: DeprecationWarning: PyArray_FromDimsAndDataAndDescr: use PyArray_NewFromDescr.
  for row in icon.get_pixels_array():
Traceback (most recent call last):
  File "/usr/bin/specto", line 30, in <module>
    specto = Specto()
  File "/usr/lib/python2.6/dist-packages/spectlib/main.py", line 128, in __init__
    self.watch_db.create(values)
  File "/usr/lib/python2.6/dist-packages/spectlib/watch.py", line 292, in create
    type = values[i]['type']
KeyError: 'type'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 100, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL), 'w')
OSError: [Errno 13] Permission denied: '/var/crash/_usr_bin_specto.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/specto", line 30, in <module>
    specto = Specto()
  File "/usr/lib/python2.6/dist-packages/spectlib/main.py", line 128, in __init__
    self.watch_db.create(values)
  File "/usr/lib/python2.6/dist-packages/spectlib/watch.py", line 292, in create
    type = values[i]['type']
KeyError: 'type'

```

---

